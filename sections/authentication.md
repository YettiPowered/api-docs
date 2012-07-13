# Authentication

The Yetti ReST API uses a Hash Message Authentication Code (HMAC) to authenticate requests. This code allows us to confirm 
both your identity and the integrity of the data sent in the request.

Before you can perform any authenticated requests, you must first obtain a web service Access Key (username) and Private Key.

To authenticate a request, you first construct your request URI and concatenate the parameters of the request onto this string 
with ampersands (&) and then use your private key to calculate the HMAC for that string, which we call the signature. 
You then include the access key and signature in an X-Authorization header when making the request.

When the request is received, the Yetti system uses a similar process to calculate a signature and compares it against the signature you sent. 
If the two signatures match, the system concludes that the requester must have access to the private key and therefore performs the request 
with the authority of the person identified by the access key. If the signatures do not match, the request is dropped and an authentication 
error is returned.

Note that it is very important that you keep your private key safe and never send it along with a request. In the event of someone else finding 
out or intercepting your private key, please contact us immediately so that we can revoke the key and provide you with a new one.

Example request signing:
```
requestUri = "https://yoursite.secure.yetti.co.uk/...ws" +
             "?paramKey=paramValue" + 
             "&timestamp=" + currentTime;

signature  = calculateHmac('sha256', requestUri, yourPrivateKey);
authHeader = "X-Authorization: username:signature"
```

Please note that you must include all parameters in the request URI before signing.

## Request

To authenticate, you must provide a timestamp parameter and an X-Authorization header comprising your username and request signature.

```
GET /1.0/Items.ws?timestamp=1330005721 HTTP/1.1
Host: demo.secure.yetti.co.uk
X-Authorization: test:b2132f1dec3f2fd6f718f268be7df11001ad57ad143f3f21ba819e65de5d151d
```

## Response

The Yetti API may return any of the HTTP/1.1 response codes defined by RFC-2616 Section 10.

```xml
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 23 Feb 2012 14:02:01 GMT
Content-Type: text/xml; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
Vary: Accept-Encoding
Expires: Thu, 01 Jan 1970 00:00:00 +0000
Cache-Control: no-cache, no-store, must-revalidate

<?xml version="1.0"?>
<yetti>
  <types>
    <id>1</id>
    <name>Blog</name>
    <nameSingular>article</nameSingular>
    <urlPath/>
    <isPurchasable/>
    <isAssetType/>
    <collectionTypeId>1</collectionTypeId>
  </types>
</yetti>
```
