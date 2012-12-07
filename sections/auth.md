# Auth API

## Available methods in the sample API

* `GET /auth/details.ws` provides some basic information about the user currently authenticated against the API.

### Get auth details
```
GET /auth/details.ws
```
```json
{
   "user":{
      "resourceId":1,
      "identifier":"username",
      "resourceTypeId":3,
      "resourceTypeName":"Administrator",
      "languageId":1,
      "languageActive":true,
      "name":"Peter Blogs",
      "created":"1970-01-01T01:02:03+01:00",
      "email":"example@example.org",
      "gravatarUrl":"http://www.gravatar.com/avatar/fb3ad7ccd5e04k5a67a9bfbd03a1f744"
   },
   "scopes":[
		"items"
   ]
}
```