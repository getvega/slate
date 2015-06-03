# Manage your users

## Model

> User example

```
{
  "id": 1,
  "firstName": "Pierre",
  "lastName": "Dupont",
  "address": "27 rue du Chemin Vert, 75011 Paris",
  "createdAt": "2015-06-03T17:30:31.000Z",
  "updatedAt": "2015-06-03T17:30:31.000Z",
  "email": "pierre@dupont.com",
  "orders": [<Order>]
}
```

Field | Required | Type | Details
----- | ---- | ---- | -----------
`firstName` | NO | string | 
`lastName` | NO | string | 
`address` | YES | string | address will be used to pickup the shipments
`email` | YES | string | 
`password` | NO | string | if you want the user to be able to log-in on cubyn.com

## Methods 

> Example of an User create HTTP request

```
POST /users HTTP/1.1
Authorization: Basic XXXXXXXXXXXXXXXXXXXXXX
Content-Type: application/json

{"firstName":"Pierre","lastName":"Dupont","email":"pierre@dupont.com"}
```

Method | Path | Description
------ | ---- | -----------
GET     | `/users`     | List all users owned by your application
POST    | `/users`     | Create a new user belonging to your application
GET     | `/users/:id` | Read details for this user _Response will include `orders` sub-documents_
PUT     | `/users/:id` | Update this user
DELETE  | `/users/:id` | Delete this user