# Entries
The API expose 4 endpoints for interacting with entries. Check out [Errors](/errors) for more info about
what status code and error response mean

## Insert an entry
To insert an entry in an entity you will have to create a form data and append to it, keys that match
the field names on the schema of the entity. We will use our Product entity as example here.
Our Product schema is the following
```json
{
    "name":"Text",
    "price":"Number",
    "image":"Image",
    "description":"Text",
    "in_discount":"Boolean"
}
```
Here is an example of how we will insert an entry in the Product entity using JavaScript on Node
```js
import { openAsBlob } from "node:fs" //node^19.8
import { readFile } from "node:fs/promises"
const form_data = new FormData()
const file = await openAsBlob('/path/to/image')
//Image upload can be done multiple ways
//import * as fs from "fs"
//const file = fs.createReadStream('/path/to/image')
form_data.append('image', file)
form_data.append('name', "Product name")
form_data.append('price', '1200')
form_data.append('description', 'Some description')
form_data.append('in_discount', 'true')

fetch(
    'https://api.yootcms.xyz/v1/entities',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        },
        method:"POST",
        body: form_data
    }
)
```

## Getting entries in an entity
Example using fetch with JavaScript
```js
fetch(
    'https://api.yootcms.xyz/v1/entities/:entity_name/entries',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        }
    }
)
```

## Update an entry
Example using fetch with JavaScript
```js
//Construct the body as a form data with the field we want to update
const form_data = new FormData()
form_data.append('name', "New product name")
form_data.append('in_discount', 'false')
fetch(
    'https://api.yootcms.xyz/v1/entities/:entity_name/entries/:entry_id',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        },
        method:"PUT",
        body: form_data
    }
)
```


## Delete an entry
Example using fetch with JavaScript
```js
fetch(
    'https://api.yootcms.xyz/v1/entities/:entity_name/entries/:entry_id',
    {
        headers:{
            "Authorization": "API_KEY_HERE"
        },
        method:"DELETE",
    }
)
```
