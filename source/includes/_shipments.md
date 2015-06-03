# Manage your shipments

## Model

> Shipment example

```
{
  "name": "iPhone 7",
  "shippingDetails": {
    "mode": "express",
    "address": "3 place de la Republique, 69002 Lyon"
  },
  "reference": "XYZ",
  "order": <Order>
}
```

Field (* = required) | Type | Details
----- | ---- | -----------
`name` | `string` | a simple description of what's inside the shipment
`shippingDetails` | `mixed` |
` -- mode` | `Enum<string>` | enum values: `eco` (within 48 hours) or `express` (24h) _Default: `eco`_
` -- address` | `string` | a geocodable address. If not defined, it will default to user's address
`reference` | `string` | a user reference he can use to track his shipments

## Methods 

> Editing a shipment in a previously created order

```
POST /orders/1/shipments/1 HTTP/1.1
Authorization: Basic XXXXXXXXXXXXXXXXXXXXXX
Content-Type: application/json

{"reference":"XYZ", "name":"Oops"}
```

Method | Path | Description
------ | ---- | -----------
GET     | `/orders/:id/shipments` | List all the shipments of this order
POST    | `/orders/:id/shipments` | Create a new Shipment within this order (will fail if order is already in `SETTLED` state)
GET     | `/orders/:id/shipments/:id` | Read details of this shipment _Response will include `order` sub-document_
PUT     | `/orders/:id/shipments/:id` | Edit a shipment
DELETE     | `/orders/:id/shipments/:id` | Delete a shipment