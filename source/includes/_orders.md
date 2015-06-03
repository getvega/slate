# Manage your orders

## Model

> Order example

```
{
  "id": 1,
  "status": "PICKING",
  "pickingDetails": {
    "address": "27 rue du Chemin Vert, 75011 Paris",
    "day": "27/09/2015",
    "timeslot": "11-14",
    "messengerType": "2-wheeled"
  },
  "createdAt": "2015-06-03T17:30:31.000Z",
  "updatedAt": "2015-06-03T17:30:31.000Z",
  "user": <User>,
  "shipments": [<Shipment>]
}
```

Field (* = required) | Type | Details
----- | ---- | -----------
`status` | `Enum<string>` | _(read-only)_ `EDITING › SETTLED › PICKING › PACKING › DELIVERING › COMPLETE`
`pickingDetails *` | `mixed` |
` -- address` | `string` | a geocodable address. If not defined, it will default to user's address
` -- day *` | `string` | `day`/`timeslot` has 1/ to be in the future, 2/ on a working day
` -- timeslot *` | `Enum<string>` | enum values: `8-11`, `11-14` or `14-17`
` -- messengerType *` | `Enum<string>` | enum values: `2-wheeled` or `4-wheeled`
`shipments` | `Array<Shipment>` | See [Shipment Model](#manage-your-shipments)


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
GET     | `/orders`                 | List all orders created through your application
GET     | `/orders/:id`             | Read details of this order _Response will include `user` and `shipments` sub-documents_
PUT     | `/orders/:id`             | Update this order
DELETE  | `/orders/:id`             | Delete this order
GET     | `/users/:id/orders`       | List all orders this user has created
POST    | `/users/:id/orders`       | Create a new order on behalf of that user