# Entities
The API exposes 3 endpoints for interacting with entities

## Create an entity
Send a POST request to the `/entities` endpoint. The request body must be a form data that contains 
the `name` of the entity and it's schema. If you don't know what a schema is please refer to this part 
of the documentation [Entities](https://docs.yootcms.xyz/entities.html).

Here is an example using `fetch` in JavaScript
```js
const entity_name = "Product"
const schema = {
    "name":"Text",
    "price":"Number",
    "image":"Image",
    "description":"Text",
    "in_discount":"Boolean"
}
const form_data = new FormData()
form_data.append('name', entity_name)
form_data.append('schema', schema)
fetch(
    'https://api.yootcms.xyz/entities',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        },
        method:"POST",
        body: form_data
    }
)
```
YOOT will return status codes and specific error messages for you to know if the operation was
successful or not. Check the [Errors](/errors.html) page for more information.


## Get entities
Example using `fetch` in JavaScript
```js
fetch(
    'https://api.yootcms.xyz/entities',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        }
    }
)
```

**NOTE** : Entities names are unique per project which justifies the use of the entities names
instead of their id

## Update an entity
Example using `fetch` in JavaScript. For the moment only the name of an entity can be modified.
```js
const new_name = "New name"
const form_data = new FormData()
form_data.append('name', new_name)
fetch(
    'https://api.yootcms.xyz/entities/:entity_name',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        },
        method:"PUT",
        body:form_data
    }
)
```

## Delete an entity
Deleting an entity will delete every data related to that entity. This action is not reversible.
Example using `fetch` in JavaScript
```js
fetch(
    'https://api.yootcms.xyz/entities/:entity_name',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        },
        method:"DELETE"
    }
)
```
