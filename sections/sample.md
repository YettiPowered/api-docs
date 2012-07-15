# Sample API

> Hello world!

## Test API

* `GET /sample/test.ws` says hello world!
* `GET /sample/hello/[name].ws` says hello to the specified name.

These sample APIs are intended for testing. No authentication is required.

### Hello world
```
GET /sample/test.ws
```
### Response
```json
{
    "test": "Hello world"
}
```

### Hello Sam
```
GET /sample/hello/Sam.ws
```

### Response
```json
{
    "hello": "Hello Sam"
}
```
