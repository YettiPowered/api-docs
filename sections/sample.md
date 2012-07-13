# Sample API

> Hello world!

## Test API

* `GET /sample/test.ws` says hello world!
* `GET /sample/hello/[name].ws` says hello to the specified name.

These sample APIs are intended for testing. No authentication is required.

### Hello world in XML

```xml
<?xml version="1.0"?>
<yetti>
  <test>Hello world</test>
</yetti>
```

### Hello world in JSON

```json
{"test":"Hello world"}
```

### Hello Sam in XML

```xml
<?xml version="1.0"?>
<yetti>
  <hello>Hello Sam</hello>
</yetti>
```
