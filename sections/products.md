# Products API

> Purchasable items

## Note

Products are essentially the same thing as any other type of item, and as such, the API endpoints for creating, retrieving and updating products are the same as for managing regular items.
The only difference is in the additional data that can be sent and received regarding stock, VAT, pricing, variations and user prompts.

## Available methods

* `GET /items/combinations/[item-id].ws` lists combinations for the given product item.
* `PUT /items/combinations/[item-id]/[combination-id].ws` updates SKU, stock and availability info for a product combination.

## Details

### List product combinations
```
GET /items/combinations/1.ws
```
```json
{
   "useStockControl":true,
   "listing":{
      "totalItems":5,
      "start":0,
      "limit":30,
      "currentMax":5,
      "totalPages":1,
      "currentPage":1,
      "items":[
         {
            "id":189,
            "available":true,
            "stock":20,
            "sku":"sku005",
            "price":54.99,
            "options":[
               {
                  "Colour":"Blue"
               },
               {
                  "Size":"Small"
               }
            ]
         },
         {
            "id":188,
            "available":true,
            "stock":5,
            "sku":"sku004",
            "price":54.99,
            "options":[
               {
                  "Colour":"Black"
               },
               {
                  "Size":"Massive"
               }
            ]
         },
         {
            "id":187,
            "available":true,
            "stock":19,
            "sku":"sku003",
            "price":54.99,
            "options":[
               {
                  "Colour":"Black"
               },
               {
                  "Size":"Small"
               }
            ]
         },
         {
            "id":190,
            "available":true,
            "stock":10,
            "sku":"sku002",
            "price":54.99,
            "options":[
               {
                  "Colour":"Blue"
               },
               {
                  "Size":"Massive"
               }
            ]
         },
         {
            "id":186,
            "available":true,
            "stock":1000,
            "sku":"sku001",
            "price":54.99,
            "options":[

            ]
         }
      ]
   }
}
```

### Update product combinations
```
PUT /items/combinations/1/189.ws
```
This will update a product combination based on the parameters passed.
```json
{
   "combination":{
      "id":189,
      "sku":"sku005",
      "stock":20,
      "options":[
         {
            "id":150,
            "name":"Blue"
         },
         {
            "id":151,
            "name":"Small"
         }
      ]
   }
}
```
You'll receive a `200 OK` if the update was a success, or one of the `400` range error codes on fail.
