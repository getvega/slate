---
title: Cubyn API

includes:
  - authentication
  - users
  - orders
  - shipments
  - errors

search: true
---

# Introduction

Welcome to the Cubyn API! This API is organized around REST. All our API endpoints expect JSON and will issue responses formatted as JSON.

## Getting started

- Ask your API credentials at api@cubyn.com, describing your needs
- Authenticate yourself via [HTTP Basic](#authentication)
- Manage your [users](#manage-your-users)
- Issues your [orders](#manage-your-orders)

## Basically

- You create [users](#manage-your-users)
- Users can create [orders](#manage-your-orders): an _Order_ defines a batch of packages (_Shipments_) to be 1/ picked up at a predefined address, 2/ packed within our facilities and then 3/ shipped through our carrier partnerships
- A _Shipment_ defines a package to be delivered to _one_ address

## Lifecycle of an Order

State | Description
----- | -----------
`EDITING` | User just created an order but has not submitted it yet
`SETTLED` | User has submitted it, but Cubyn has not processed the order yet
`PICKING` | Cubyn assigned a messenger to collect the shipments
`PACKING` | The messenger has picked the shipments and delivered to our logisticians
`DELIVERING` | The shipments have been posted through the carrier
`COMPLETE` | All shipments has arrived at destination