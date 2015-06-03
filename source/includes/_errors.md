# Errors

> When `PUT`ing or `POST`ing - in case of a validation error, our API will describe each erroneous field. Here is an example:

> `POST /users` with `{ "email": "incorrect@adress", "password": "areallylongpassword" }`

```json
{
  "message": "Validation error: Validation isEmail failed,\nValidation error: Validation len failed",
  "type": "ValidationError",
  "errors": [
    {
      "field": "email",
      "message": "Validation isEmail failed"
    },
    {
      "field": "password",
      "message": "Validation len failed"
    }
  ]
}

```

Code | Type | Description
---- | ---- | -----------
400 | `BadRequestError`           | Often missing a required parameter
400 | `ValidationError`           | Some field is badly formatted or has validation errors
404 | `EndpointNotFoundError`     | The requested url does not exist
404 | `ResourceNotFoundError`     | The requested resource does not exist
403 | `ForbiddenError`            | You cannot perform that action on the 
50X | `ServerError`               | Oops - that's for us. 
