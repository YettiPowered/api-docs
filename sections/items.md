# Items API

> Hello world!

## Test API

* `GET /items.ws` lists item types.
* `GET /items/[type-id].ws` lists items of the given type.
* `GET /items/[type-id]/[item-id].ws` fetches the item with the given ID.
* `POST /items/[type-id].ws` creates an item of the given type.
* `PUT /items/[type-id]/[item-id].ws` updates the item with the given ID.
* `DELETE /items/[type-id]/[item-id].ws` deletes the item with the given ID.
* `GET /items/collections/[item-id].ws` fetch a list of categories to which the given item is assigned.
* `PUT /items/collections/[item-id].ws` assign the item to one or more categories.

### List item types
```
GET /items.ws
```
### Response
```json
{
    "types": [
        {
            "collectionTypeId": "1", 
            "id": "1", 
            "isAssetType": "0", 
            "isPurchasable": "0", 
            "name": "Blog", 
            "nameSingular": "post", 
            "urlPath": ""
        },
        {
            "collectionTypeId": "2", 
            "id": "2", 
            "isAssetType": "0", 
            "isPurchasable": "1", 
            "name": "Products", 
            "nameSingular": "product", 
            "urlPath": "/shop/catalogue"
        }
    ]
}
```