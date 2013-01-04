# Categories API

> Categories are actually called "collections"...

## Available methods

* `GET /collections.ws` lists collection types.
* `GET /collections/[type-id].ws` lists collections of the given type.
* `GET /collections/items/[collection-id].ws` fetch the list of items within the given collection.
* `PUT /collections/items/[collection-id].ws` update the list of items within the given collection.

## Details

### List collection types
```
GET /collections.ws
```
```json
{
   "types":[
      {
         "id":1,
         "name":"Images",
         "nameSingular":"image",
         "itemTypeClassId":1
      },
      {
         "id":2,
         "name":"Categories",
         "nameSingular":"category",
         "itemTypeClassId":2
      }
   ]
}
```

### List collections
```
GET /collections/2.ws
```
```json
{
   "listing":{
      "totalItems":3,
      "start":0,
      "limit":30,
      "currentMax":3,
      "totalPages":1,
      "currentPage":1,
      "items":[
         {
            "resource":{
               "resourceId":22,
               "identifier":"our-products",
               "resourceTypeId":4,
               "resourceTypeName":"Categories",
               "languageId":1,
               "languageActive":true,
               "name":"Our Products",
               "created":"1970-01-01T01:00:01+01:00",
               "structural":true
            },
            "metaInfo":{
               "title":"",
               "description":""
            },
            "revision":{
               "revisionId":14,
               "created":"2012-06-18T14:40:36+01:00",
               "comment":null,
               "author":{
                  "id":16,
                  "name":"a-user",
                  "gravatarUrl":"http://www.gravatar.com/avatar/947f2d5d2e15fb8d6da7a40521b36e05"
               }
            },
            "parentId":-1
         },
         {
            "resource":{
               "resourceId":21,
               "identifier":"construction",
               "resourceTypeId":4,
               "resourceTypeName":"Categories",
               "languageId":1,
               "languageActive":true,
               "name":"Construction",
               "created":"1970-01-01T01:00:01+01:00",
               "structural":true
            },
            "metaInfo":{
               "title":"Industrial",
               "description":""
            },
            "revision":{
               "revisionId":8,
               "created":"2012-06-26T12:05:47+01:00",
               "comment":null,
               "author":{
                  "id":15,
                  "name":"a-user",
                  "gravatarUrl":"http://www.gravatar.com/avatar/947f2d5d2e15fb8d6da7a40521b36e05"
               }
            },
            "parentId":22
         },
         {
            "resource":{
               "resourceId":20,
               "identifier":"agricultural",
               "resourceTypeId":4,
               "resourceTypeName":"Categories",
               "languageId":1,
               "languageActive":true,
               "name":"Agricultural",
               "created":"1970-01-01T01:00:01+01:00",
               "structural":true
            },
            "metaInfo":{
               "title":"",
               "description":""
            },
            "revision":{
               "revisionId":18,
               "created":"2012-08-28T12:10:05+01:00",
               "comment":null,
               "author":{
                  "id":18,
                  "name":"a-user",
                  "gravatarUrl":"http://www.gravatar.com/avatar/947f2d5d2e15fb8d6da7a40521b36e05"
               }
            },
            "parentId":22
         }
      ]
   }
}
```

### List items within a collection
```
GET /collections/items/20.ws
```
This will return a list of IDs for items within the collection.
```json
{
   "items":[
      85,
      1793
   ]
}
```

### Update the list of items within a collection
```
PUT /collections/items/20.ws
```
```json
{
   "items":[
      85,
      1793
   ]
}
```
You'll receive a `200 OK` if the update was a success.
