# Item filters API

> These allow you to filter out random cruft from a larger data set.

## Available methods

* `GET /filters/[type-id].ws` lists filter types for the given type.
* `POST /filters/[type-id].ws` creates a filter type for the given item type.
* `GET /filters/[type-id]/[filter-type-id].ws` lists filters of the given type.
* `POST /filters/[type-id]/[filter-type-id].ws` creates a filter within the given filter type.
* `PUT /filters/[type-id]/[filter-type-id].ws` updates the filter type with the given ID.
* `DELETE /filters/[type-id]/[filter-type-id].ws` deletes the filter type with the given ID.
* `GET /filters/[type-id]/[filter-type-id]/[filter-id].ws` lists items that are assigned to the given filter.
* `PUT /filters/[type-id]/[filter-type-id]/[filter-id].ws` updates the filter with the given ID.
* `DELETE /filters/[type-id]/[filter-type-id]/[filter-id].ws` deletes the filter with the given ID.

Filters can also be configured within categories. To do this, use any of the above URIs but replace `/filters/[type-id]` with `/collections/filters/[collection-id]`.

## Details

### List filter types
```
GET /filters/5.ws
```
```json
{
    "types": [
        {
            "id": 1,
            "name": "Colour"
        },
        {
            "id": 2,
            "name": "Brand"
        }
    ]
}
```

### Create a filter type
```
POST /filters/5.ws
```
This will create a new filter type from the parameters passed:
```json
{
    "name": "Size"
}
```
You'll receive a `201 Created` header, along with an `X-ResourceId` and `Location` containing a URL to find the new filter type via the API.

### List filters for a particular filter type
```
GET /filters/5/1.ws
```
```json
{
    "filters": [
        {
            "conditionalFilters": [],
            "id": 1,
            "name": "Red"
        },
        {
            "conditionalFilters": [],
            "id": 2,
            "name": "Green"
        },
        {
            "conditionalFilters": [],
            "id": 3,
            "name": "Blue"
        }
    ],
    "id": 1,
    "name": "Colour"
}
```

### Create a filter within a particular filter type
```
POST /filters/5/3.ws
```
This will create a new filter from the parameters passed:
```json
{
    "name": "Small"
}
```
You'll receive a `201 Created` header, along with an `X-ResourceId` and `Location` containing a URL to find the new filter via the API.

### Update a filter type
```
PUT /filters/5/3.ws
```
This will update the particular filter type based on the parameters passed:
```json
{
    "name": "Smallish"
}
```
You'll receive a `200 OK` if the update was successful, or an error code and an array of errors in JSON if it fails.

### Delete a filter type
```
DELETE /filters/5/3.ws
```
Will delete the filter type with the given ID and return `200 OK` on success.

### List items that are assigned to a particular filter
```
GET /filters/5/1/2.ws
```
```json
{
    "conditionalFilters": [],
    "filterTypeId": 1,
    "id": 2,
    "items": [
        9,
        11
    ],
    "name": "Green"
}
```

# Update a filter
```
PUT /filters/5/3/7.ws
```
This will update the filter (in this case filter ID 7) based on the data passed:
```json
{
    "conditionalFilters": [
        1,
        2
    ],
    "items": [
        9,
        11
    ],
    "name": "Small"
}
```
You'll receive a `200 OK` if the update was successful, or an error code and an array of errors in JSON if it fails.

### Delete a filter
```
DELETE /filters/5/3/7.ws
```
Will delete the filter with the given ID and return `200 OK` on success.
