# The Yetti webservice API

Yetti is a web-based Software as a Service (SaaS) e-commerce and publishing platform.
In addition to the built in administration tools, Yetti allows users to manage content via a simple web service (ReST: Representational State Transfer) interface.

For more details on Yetti, please refer to http://yetti.co.uk. We welcome comments, feedback and bug reports at support@yetti.co.uk.

## Intended audience

This guide is intended to assist software developers who want to write applications using the Yetti API.
To use the information provided here, you should first have a general understanding of the Yetti platform and have access to an active administration account with web service credentials. 
You should also be familiar with:

* ReSTful web services
* HTTP/1.1
* XML and/or JSON data serialization formats

# Concepts

To use the Yetti API effectively, you should understand several key concepts:

## Authentication

Authentication is the process of proving your identity to the system. 
Identity is an important factor when performing web service requests, as it is your identify which governs what access you have and what operations you are allowed to perform.

Some basic Yetti API operations don't require authentication, however any method which alters data, and most which return data specific to your system do require particular privileges. 
The authentication and signing process is explained in more detail in the [authentication guide](https://github.com/YettiPowered/api-docs/blob/master/sections/authentication.md).

## Resources

Most individual pieces of content in Yetti are known as "resources". Resources can usually be created, updated and deleted, unless specific permissions dictate otherwise.

### Items

Items are the "bread and butter" resources in Yetti. Everything from blog articles to FAQs to purchasable products are usually item resources.
Items are always created with a particular "type", and this type is dynamically configured with properties, such as "Name", "Description", etc, based on the needs of the particular website.

### Categories

Categories (sometimes referred to as collections) are used to organise items. 
Each type of item has an independent category hierarchy which itself acts a lot like a directory tree on a computer file system. 
Items can be placed into one or more categories.

### Pages

Pages are basic content manageable resources.

### Users

User accounts can be customised in the same way as any other type of resource (custom properties, assets, etc).

### Groups

Groups can be used to organise users into sets. This can be useful when applying tiered product pricing or creating promotions which are only available to a subset of customers.

# General API information

The Yetti API is implemented using a ReSTful web service interface. 
Resources can be accessed using a unique identifier (URI) and manipulated by making requests using one of the available HTTP verbs (GET, POST, PUT, DELETE).

Web service requests are always identified by the URI suffix "`.ws`".

## Request / Reponse types

As of the most recent API version (2), Yetti supports the JSON serialization format only.

### cURL examples

The following examples show how to use cURL to interface with the Yetti API.

#### cURL request/response
```
curl -D - \ https://demo.secure.yetti.co.uk/1.0/Sample/Test.ws?format=json

HTTP/1.1 200 OK
Server: nginx
Date: Thu, 23 Feb 2012 09:27:26 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
Vary: Accept-Encoding
Expires: Thu, 01 Jan 1970 00:00:00 +0000
Cache-Control: no-cache, no-store, must-revalidate
```
JSON response:
```json
{"test":"Hello world"}
```

## Paginated resources

To reduce load on the service, list operations will return a maximum of 30 resources at a time. To navigate the list, a page parameter can be provided in the URI, e.g. `?page=2`.

## API version

The Yetti API uses a URI versioning scheme. The first element of the path contains the target version number (e.g. `https://demo.secure.yetti.co.uk/2/...`). 
If a version number is not provided, the latest version is assumed.

New features and functionality that do not break API-compatibility will be introduced in the current version of the API and the URI will remain unchanged. 
Any feature or functionality changes that would necessitate a break in API-compatibility will require a new version, which will result in the URI version 
being updated accordingly. When new API versions are released, older versions will be marked as `DEPRECATED`.

# Available APIs

[Sample](https://github.com/YettiPowered/api-docs/blob/master/sections/sample.md)

# Contributing

The Yetti APIs are under active development, as are these docs. If you find a bug or have specific comments, please use GitHub issues. If you'd like to help us make these docs
better then feel free to fork and send pull requests.
