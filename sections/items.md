# Items API

> Items, items everywhere - but not a stitch to wear.

## Available methods

* `GET /items.ws` lists item types.
* `GET /items/[type-id].ws` lists items of the given type.
* `GET /items/[type-id]/[item-id].ws` fetches the item with the given ID.
* `POST /items/[type-id].ws` creates an item of the given type.
* `PUT /items/[type-id]/[item-id].ws` updates the item with the given ID.
* `DELETE /items/[type-id]/[item-id].ws` deletes the item with the given ID.
* `GET /items/collections/[item-id].ws` fetch a list of categories to which the given item is assigned.
* `PUT /items/collections/[item-id].ws` assign the item to one or more categories.
* `GET /templates/item/[type-id].ws` fetch a blank template for an item of the given type.

## Details

### List item types
```
GET /items.ws
```
```json
{
    "types": [
        {
            "collectionTypeId": 1, 
            "id": 1, 
            "isAssetType": "", 
            "isPurchasable": "", 
            "name": "Blog", 
            "nameSingular": "post", 
            "urlPath": "/blog/posts"
        },
        {
            "collectionTypeId": 2,
            "id": 2,
            "isAssetType": "", 
            "isPurchasable": 1, 
            "name": "Products", 
            "nameSingular": "product", 
            "urlPath": "/shop/catalogue"
        }
    ]
}
```

### List items
```
GET /items/1.ws
```
```json
{
    "listing": {
        "currentMax": 2, 
        "currentPage": 1, 
        "items": [
            {
                "assets": "", 
                "collectionIds": [], 
                "properties": "", 
                "resource": {
                    "author": {
                        "gravatarUrl": "http://www.gravatar.com/avatar/3bbad78cd5e0455aa719bfbd03a1f744", 
                        "id": 1, 
                        "name": "Sam Holman"
                    }, 
                    "commentCount": 0, 
                    "created": "2012-07-13T15:12:35+01:00", 
                    "fileExtension": "html", 
                    "identifier": "welcome-to-yetti", 
                    "languageId": 1, 
                    "name": "Welcome to Yetti", 
                    "resourceId": 177, 
                    "resourceTypeId": 1, 
                    "resourceTypeName": "Blog", 
                    "urlPath": "/blog/articles/welcome-to-yetti.html"
                }, 
                "revision": {
                    "author": {
                        "gravatarUrl": "http://www.gravatar.com/avatar/3bbad78cd5e0455aa719bfbd03a1f744", 
                        "id": 1, 
                        "name": "Sam Holman"
                    }, 
                    "comment": "", 
                    "created": "2012-07-13T15:12:35+01:00", 
                    "revisionId": 1
                }
            }, 
            {
                "assets": "", 
                "collectionIds": [
                    42
                ], 
                "properties": "", 
                "resource": {
                    "author": {
                        "gravatarUrl": "http://www.gravatar.com/avatar/179ea009f8c46c7a6f0e61afff6ceced", 
                        "id": 7, 
                        "name": "Paul Rufus"
                    }, 
                    "commentCount": 0, 
                    "created": "2012-06-29T08:52:28+01:00", 
                    "fileExtension": "html", 
                    "identifier": "saturday-and-sunday-best-times-to-tweet", 
                    "languageId": 1, 
                    "name": "Saturday and Sunday: the best times to tweet", 
                    "resourceId": 154, 
                    "resourceTypeId": 1, 
                    "resourceTypeName": "Blog", 
                    "urlPath": "/blog/articles/saturday-and-sunday-best-times-to-tweet.html"
                }, 
                "revision": {
                    "author": {
                        "gravatarUrl": "http://www.gravatar.com/avatar/3bbad78cd5e0455aa719bfbd03a1f744", 
                        "id": 1, 
                        "name": "Sam Holman"
                    }, 
                    "comment": "", 
                    "created": "2012-07-12T08:59:42+01:00", 
                    "revisionId": 3
                }
            }, 
        ], 
        "limit": 30, 
        "start": 0, 
        "totalItems": 2, 
        "totalPages": 1
    }
}
```

### Fetch an individual item
```
GET /items/1/69.ws
```
```json
{
    "item": {
        "assets": [], 
        "collectionIds": [
            38, 
            39, 
            42
        ], 
        "properties": {
            "Author": {
                "dataType": "string", 
                "id": 3, 
                "value": ""
            }, 
            "Body": {
                "dataType": "longstring", 
                "id": 5, 
                "value": "<div>Martin (one of our front end developers) is up for a challenge so we've tried to make it tricky.\u00a0</div><div>He's going to attempt to build a fully operational e-commerce site in under an hour.</div><div><br /></div><div>The brief is:<br /></div><ul><li>A site populated with five products.</li><li>There will be no predefined design so Martin is able to create the site as he goes along and make any design decisions himself.</li><li>As a result of the above, it'll be a very simple front-end look and feel.</li><li>Dummy site content will be pre-written and provided in a text file.</li><li>No use of JavaScript.<br /></li><li>Modern browsers only.</li></ul><div>It's obviously worth noting that a real site would need additional time for polish and population, but building anything in an hour is a pretty impressive feat. Will he manage it?\u00a0</div><div><br /></div><div>Find out on 12th June 2012. We will tweet out the URL to the development site, so you can see the progress in real time.</div><div><br /></div><div><strong>Update: </strong>Martin will be starting the challenge at 2PM today (June 12th). You can view the site live at <a href=\"http://onehour.dev.yetti.co.uk\">onehour.dev.yetti.co.uk</a>, just hit refresh every now and then to see his progress and please feel free to tweet words of encouragement or any comments to <a href=\"http://twitter.com/YettiPowered\">@YettiPowered</a>. We'll also be recording his screen and aiming to upload that to YouTube as soon as we can afterwards.</div><div><br /></div><div><strong>Update 2:</strong> He completed the challenge! The finished site is at<a href=\"http://onehour.dev.yetti.co.uk\"> onehour.dev.yetti.co.uk</a> and you can watch the video recording of his screen while he was working below. :-)</div><div><br /></div><div><strong>Update 3:</strong> Although functional as a shop after an hour, Martin then spent an extra 45 minutes on the site, adding a mini basket to the header, category navigation to the products page, a contact page with a form, an about page and some extra polish to make the site look a little nicer.</div>"
            }, 
            "Date": {
                "dataType": "date", 
                "id": 2, 
                "value": 1338988028
            }, 
            "Name": {
                "dataType": "string", 
                "id": 1, 
                "value": "How fast can you build an e-commerce site?"
            }, 
            "Summary": {
                "dataType": "longstring", 
                "id": 4, 
                "value": "<div>How fast can an e-commerce site be built? We thought it might be fun to see how quickly a simple store could be built from scratch using Yetti.</div>"
            }, 
            "YouTube_video_ID": {
                "dataType": "string", 
                "id": 6, 
                "value": "v2938XRpRjM"
            }
        }, 
        "resource": {
            "author": {
                "gravatarUrl": "http://www.gravatar.com/avatar/a904cac47116105dfcf01ebd93738f87", 
                "id": 5, 
                "name": "Martin Blackburn"
            }, 
            "commentCount": 2, 
            "created": "2012-06-06T09:20:13+01:00", 
            "fileExtension": "html", 
            "identifier": "how-fast-can-you-build-an-ecommerce-site", 
            "languageId": 1, 
            "name": "How fast can you build an e-commerce site?", 
            "resourceId": 69, 
            "resourceTypeId": 1, 
            "resourceTypeName": "Blog", 
            "urlPath": "/blog/articles/how-fast-can-you-build-an-ecommerce-site.html"
        }, 
        "revision": {
            "author": {
                "gravatarUrl": "http://www.gravatar.com/avatar/a904cac47116105dfcf01ebd93738f87", 
                "id": 5, 
                "name": "Martin Blackburn"
            }, 
            "comment": "Changing youtube link to embed instead.", 
            "created": "2012-06-28T14:07:08+01:00", 
            "revisionId": 16
        }
    }
}
```
