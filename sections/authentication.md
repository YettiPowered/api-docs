# Authentication

The Yetti ReST API supports authentication via two methods - [OAuth 2](http://oauth.net) and [HMAC](http://en.wikipedia.org/wiki/Hash-based_message_authentication_code).
The decision to use one or the other really depends on the intended usage of your app.

OAuth is great for public integrations and web applications, as it allows a site administrator to log in with their own Yetti website account and authorise your application
to perform API operations on their behalf without having to copy/paste API keys or touch sensitive login info.

Conversely, the HMAC method of authentication is sometimes better for private integrations and automated scripts such as batch processors.
Using this approach, an access key and a private key are statically linked to a particular user account and API operations can then be performed using those details.

More details can be found on the specific documentation articles:

* [Authentication using OAuth 2](authentication_with_oauth2.md)
* [Authentication using HMAC](authentication_with_hmac.md)
