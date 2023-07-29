# Errors
Here is a list of error codes you might get back from YOOT's API and what they mean

## STATUS CODES

### 200
Means that everything went fine.

### 201
Means that a resource has been created

### 401
Invalid or missing API key in request headers

### 403
Missing required permission on API key

### 404
A resource has not been found

### 500
Internal server error. When facing this error, try again and contact support if the error persists 


## CUSTOM YOOT ERROR MESSAGES

### ERR_CONTENT_TYPE
Except for GET requests, every request you sent to the API must have their
Content-Type header set to'multipart/form-data'

### ERR_BAD_REQUEST
Is returned when the request body does not contain all required keys or does not match the 
required format 

### ERR_CREATE_PERMISSION
Means that the API key does not have permission to create data

### ERR_WRITE_PERMISSION
Means that the API key does not have permission to write to existing data

### ERR_DELETE_PERMISSION
Means that the API key does not have permission to delete data

### ERR_DUPLICATE
Is returned when you are trying to create a resource that already exists. For example creating
an entity with that name that is already being used by another entity

### ERR_EMPTY_NAME
Is returned when the `name` parameter is missing from the request body

### ERR_RESOURCE_NOT_FOUND
Is returned when a resource you are trying to access is not found. For example when trying to
fetch data from an entity that does not exist

### ERR_WRONG_FIELD_TYPE
Is returned when your request body contains data types that does not match the schema of an entity.
For example
//...refer to example in [Entities page](/entities)
```js
form_data.append('price', 'one thousand')

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
This will cause a ERR_WRONG_FIELD_TYPE because the `price` field is of type Number and we can not cast
`one thousand` into a number

### ERR_EXPECTED_IMAGE
Is returned when a field of type Image receives data that is not a file
For example
//...refer to example in [Entities page](/entities)
```js
form_data.append('image', 'Some image')

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
This will cause a ERR_EXPECTED_IMAGE because the `image` field is of type Image, thus we expect you
to send a Blob in the form data.

### ERR_IMAGE_UPLOAD
Is returned when something goes wrong while uploading your image(s). When facing this error, try again
and contact support if the error persists
