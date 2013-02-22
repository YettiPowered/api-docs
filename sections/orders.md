# Orders API

> Here are your orders boys.

## Available methods

* `GET /orders.ws` list orders.
* `POST /orders.ws` create a new order.
* `GET /orders/[order-id].ws` fetches the order with the given ID.
* `PATCH /orders/[order-id].ws` update the given order.
* `GET /templates/order.ws` fetch a blank template for use when creating a new order.
* `GET /orders/statuses.ws` lists all available order statuses for the site.

## Details

### List orders
```
GET /orders.ws
```
You can optionally provide a status ID in the URL to filter the list down to a particular status.
```
GET /orders.ws?status=[status-id]
```
```json
{
   "listing":{
      "totalItems":1,
      "start":0,
      "limit":30,
      "currentMax":1,
      "totalPages":1,
      "currentPage":1,
      "items":[
         {
            "id":1500,
            "authorisedTime":1358785952,
            "user":{
               "id":4,
               "name":"customer",
               "email":"example@example.org",
               "gravatarUrl":"https://secure.gravatar.com/avatar/928523e5486e6ebc833f8d3615dc6145",
               "addresses":{
                  "shipping":{
                     "identifier":"Home",
                     "name":"A customer",
                     "line1":"1 Test Lane",
                     "line2":"Flannel",
                     "city":"Leeds",
                     "region":"West Yorkshire",
                     "postcode":"LS1 1AB",
                     "country":"United Kingdom",
                     "countryCode":"GB",
                     "telephone":01234567890
                  },
                  "billing":{
                     "identifier":"Home",
                     "name":"A customer",
                     "line1":"1 Test Lane",
                     "line2":"Flannel",
                     "city":"Leeds",
                     "region":"West Yorkshire",
                     "postcode":"LS1 1AB",
                     "country":"United Kingdom",
                     "countryCode":"GB",
                     "telephone":01234567890
                  }
               }
            },
            "statusId":2,
            "status":"Do Not Process",
            "items":[
               {
                  "id":407,
                  "quantity":1,
                  "resource":{
                     "resourceId":2468,
                     "identifier":"testproduct",
                     "resourceTypeId":5,
                     "resourceTypeName":"Products",
                     "languageId":1,
                     "languageActive":false,
                     "name":"test-product",
                     "created":"2013-01-18T11:03:49+00:00",
                     "fileExtension":"html",
                     "urlPath":false,
                     "commentCount":0,
                     "sku":"abc123"
                  },
                  "combination":{
                     "id":15438,
                     "available":true,
                     "stock":0,
                     "sku":"abc123",
                     "price":0,
                     "options":[

                     ]
                  },
                  "prompts":[

                  ],
                  "shipped":false,
                  "price":1.01,
                  "priceIncVat":1.01,
                  "vat":0
               }
            ],
            "discounts":[

            ],
            "discountsTotal":0,
            "shipping":0,
            "vat":0,
            "subtotalOfItems":1.01,
            "subtotal":1.01,
            "totalExcVat":1.01,
            "total":1.01,
            "payment":{
               "gateway":"Paypal",
               "taken":0,
               "refunded":1.01,
               "remaining":0
            },
            "transactions":[
               {
                  "amount":1.01
               }
            ],
            "shipments":[

            ],
            "notes":[

            ],
            "history":[
               {
                  "time":1361189645,
                  "note":"Viewed order",
                  "user":{
                     "resourceId":1,
                     "identifier":"Admin",
                     "resourceTypeId":3,
                     "resourceTypeName":"Administrator",
                     "languageId":1,
                     "languageActive":true,
                     "name":"An Administrator",
                     "created":"2008-11-10T14:35:48+00:00",
                     "author":{
                        "id":1,
                        "name":"An Administrator",
                        "gravatarUrl":"https://secure.gravatar.com/avatar/47abf3ce0726bc29438b1109c8192faf"
                     },
                     "email":"example@example.com",
                     "gravatarUrl":"https://secure.gravatar.com/avatar/47abf3ce0726bc29438b1109c8192faf"
                  },
                  "auto":true
               }
            ]
         }
      ]
   }
}
```

### Fetch an individual order
```
GET /orders/1500.ws
```
```json
{
   "order":{
      "id":1500,
      "authorisedTime":1358785952,
      "user":{
         "id":4,
         "name":"customer",
         "email":"example@example.org",
         "gravatarUrl":"https://secure.gravatar.com/avatar/928523e5486e6ebc833f8d3615dc6145",
         "addresses":{
            "shipping":{
               "identifier":"Home",
               "name":"A customer",
               "line1":"1 Test Lane",
               "line2":"Flannel",
               "city":"Leeds",
               "region":"West Yorkshire",
               "postcode":"LS1 1AB",
               "country":"United Kingdom",
               "countryCode":"GB",
               "telephone":01234567890
            },
            "billing":{
               "identifier":"Home",
               "name":"A customer",
               "line1":"1 Test Lane",
               "line2":"Flannel",
               "city":"Leeds",
               "region":"West Yorkshire",
               "postcode":"LS1 1AB",
               "country":"United Kingdom",
               "countryCode":"GB",
               "telephone":01234567890
            }
         }
      },
      "statusId":2,
      "status":"Do Not Process",
      "items":[
         {
            "id":407,
            "quantity":1,
            "resource":{
               "resourceId":2468,
               "identifier":"testproduct",
               "resourceTypeId":5,
               "resourceTypeName":"Products",
               "languageId":1,
               "languageActive":false,
               "name":"test-product",
               "created":"2013-01-18T11:03:49+00:00",
               "fileExtension":"html",
               "urlPath":false,
               "commentCount":0,
               "sku":"abc123"
            },
            "combination":{
               "id":15438,
               "available":true,
               "stock":0,
               "sku":"abc123",
               "price":0,
               "options":[

               ]
            },
            "prompts":[

            ],
            "shipped":false,
            "price":1.01,
            "priceIncVat":1.01,
            "vat":0
         }
      ],
      "discounts":[

      ],
      "discountsTotal":0,
      "shipping":0,
      "vat":0,
      "subtotalOfItems":1.01,
      "subtotal":1.01,
      "totalExcVat":1.01,
      "total":1.01,
      "payment":{
         "gateway":"Paypal",
         "taken":0,
         "refunded":1.01,
         "remaining":0
      },
      "transactions":[
         {
            "amount":1.01
         }
      ],
      "shipments":[

      ],
      "notes":[

      ],
      "history":[
         {
            "time":1361189645,
            "note":"Viewed order",
            "user":{
               "resourceId":1,
               "identifier":"Admin",
               "resourceTypeId":3,
               "resourceTypeName":"Administrator",
               "languageId":1,
               "languageActive":true,
               "name":"An Administrator",
               "created":"2008-11-10T14:35:48+00:00",
               "author":{
                  "id":1,
                  "name":"An Administrator",
                  "gravatarUrl":"https://secure.gravatar.com/avatar/47abf3ce0726bc29438b1109c8192faf"
               },
               "email":"example@example.com",
               "gravatarUrl":"https://secure.gravatar.com/avatar/47abf3ce0726bc29438b1109c8192faf"
            },
            "auto":true
         }
      ]
   }
}
```

### Update an order
```
PATCH /orders/1500.ws
```
This will update the order with the given ID from the parameters passed.
```json
{
   "order":{
      "statusId":2
   }
}
```
You'll receive a `200 OK` if the update was a success, or one of the `400` range error codes on fail.

### List all available statuses
```
GET /orders/statuses.ws
```
```json
{
   "statuses":[
      {
         "id":1,
         "name":"New order"
      },
      {
         "id":3,
         "name":"Hold"
      },
      {
         "id":4,
         "name":"In Stock"
      },
      {
         "id":5,
         "name":"Invoice"
      },
      {
         "id":6,
         "name":"Chargeback"
      },
      {
         "id":7,
         "name":"PAY - Contact Customer"
      },
      {
         "id":8,
         "name":"PAY - Awaiting Customer"
      },
      {
         "id":9,
         "name":"OOS - To Order"
      },
      {
         "id":10,
         "name":"OOS - Contact Customer"
      },
      {
         "id":11,
         "name":"OOS - Awaiting Customer"
      },
      {
         "id":12,
         "name":"OOS - OK Waiting"
      },
      {
         "id":13,
         "name":"COMP - Citylink"
      },
      {
         "id":14,
         "name":"COMP - Parcelforce"
      },
      {
         "id":15,
         "name":"COMP - UK Signed For"
      },
      {
         "id":16,
         "name":"COMP - Intl Signed For"
      },
      {
         "id":17,
         "name":"COMP - First Class Mail"
      },
      {
         "id":2,
         "name":"Do Not Process"
      }
   ]
}
```