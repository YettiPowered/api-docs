# Authentication with OAuth 2

OAuth 2 provides a method for you, as an application developer, to request access to the data on a user's Yetti site without getting their password or fiddling about with API keys.

Developers first need to [register their application](http://yetti.co.uk) in order to receive a unique Client ID and Client Secret.
You must keep your Client Secret **safe and secure** - or the integrity of your application, and of your user's data, will be potentially compromised.

## The web application flow

**Step 1. Redirect users to authorise access to their Yetti site**

`GET https://yoursite.secure.yetti.co.uk/oauth/authorize.admin?client_id=id&redirect_uri=uri&scope=scopes&state=...`

Parameters:

* **client_id** - The client ID you received when setting up your application.
* **redirect_uri** - The URL in your app where users will be sent after authorisation.
* **scope** - Comma separated list of [scopes](#scopes) (used to request permission to specific types of resource).
* **state** - An unguessable random string. Used to protect against cross-site request forgery attacks. You should generate this string and store it in a local client-side session variable.

**Step 2. User logs in to their Yetti site and authorises your app.**

On directing the user to their Yetti site with the URL above, a number of things may happen:

1. If the user is already logged into their Yetti site and has already authorised your app, they will be immediately redirected back to your application with a `code` parameter in the query string.
2. If the user is logged into their Yetti site but has not previously authorised your app, they will be presented with a screen asking them if they wish to approve your app with your requested
   permissions, and assuming they do, they will then also be redirected back to your app with a `code` parameter in the query string.
3. If the user wasn't logged in to their Yetti site, they will be presented with a standard admin login form. Once logged in, they may or may not see the approval screen as above depending on whether
   or not your app has already been approved. Either way, once approved, they will also be redirected back to your app with a `code` parameter in the query string.

**Step 3. Exchange the code for an access token.**

Once the user has arrived back at your application, you need to do a couple of things:

Firstly, the state sent from your application in step 1 will have been returned in a `state` parameter.
If the state received doesn’t match the one you generated then we can assume that the request has been created by a 
third party and the process should be aborted to avoid [CSRF attacks](http://en.wikipedia.org/wiki/Cross-site_request_forgery).

Once you've validated the state and have a code from Yetti you should immediately exchange this code for an access token which can be used to make API requests.

Your app should make a server-side POST request to `https://yoursite.secure.yetti.co.uk/oauth/access_token.ws`, sending a JSON blob as follows:

```json
{
    "client_id":"your_client_id",
    "client_secret":"your_client_secret",
    "code":"temporary_code",
    "state":"your_state"
}
```

If the details match, an access token will be returned:

```json
{
   "access_token":"fbdadf3a578d01fea87a0b253506b1dac786a2cf6cde36ee83670ad6fc188289",
   "token_expires":7200,
   "token_type":"bearer"
}
```

**Step 4. Test the access token by performing an API request**

You should persist the access token you received from Yetti in your database or in a session variable in order to make further requests to the Yetti API,
acting on behalf of the user, by providing it in an `Authorization` header:

`Authorization: bearer fbdadf3a578d01fea87a0b253506b1dac786a2cf6cde36ee83670ad6fc188289`

In order to check whether or not a user is "logged in" to your application, you can perform any API request which requires authorisation and passing the access token as shown above.
A common first request is to fetch some basic information about the current authorised user via the [Auth details API](auth.md) at `/auth/details.ws`.

### Token invalidation

The access token can become invalid for a number of reasons:

1. Expiry. The token_expires flag indicates how long (in seconds) the token will be valid for. It's normally valid for two hours from the time of issue.
2. The user logs out of Yetti.
3. The user changes their password.
4. The user revokes access to your application in their admin area.

If you find that the access token becomes invalid (the API denies permission) then you can redirect the user back to the original authorization endpoint. If they're still logged in to Yetti
and they haven't revoked access to your app then they'll be returned straight back without any user interaction and with a code parameter which can be used to request a new access token in
the same way as before.

Whilst valid, the access token provides access to the user's site with all of the permissions you've requested, so it's important that you **keep it safe**.
It doesn't need, and therefor shouldn't, be transmitted anywhere other than to the Yetti API via server-side HTTPS requests.

## Scopes

Scopes are a means by which you can *limit* the access your app has to the data on a site.
Best-practice security principles should be to request access only to the specific types of resource that your application needs to function.
Note that they do not grant access to any resources that the user would not already have access to, so your app should be written in such a way that it can handle permission errors gracefully.

The available scopes are:

* items
* users
* pages

You can request your desired scopes in the initial authorisation request. I.e. When redirecting the user to login or authorise your app.
If a user has previously authorised your application but you've since changed the requested scopes then they'll be asked to re-confirm your application based on it's new requested permissions.
