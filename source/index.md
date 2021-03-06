---
YourGuy: API Reference

toc_footers:
  - <a href='mailto:tech@yourguy.in?subject=Request for API KEY'>Contact YourGuy for API Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the YourGuy API! You can use our API to access YourGuy API endpoints, which can get information on all action on <ul>
<li>orders </li>
<li>customers </li>
<li>products in our database.</li>
</ul>


# Authentication

YourGuy uses <b>Token based Authentication</b> system to allow access to the API.

Please include your API key in the HTTP HEADER of all your API requests in the following way:

`Authorization: Token <apikey>`

### Base URL
http:yourguytestserver.herokuapp.com/


# Orders

## Get All orders

This endpoint retrieves all orders for a date specified.

### HTTP Request

`GET /api/v2/order/?date=<respective-date>&page=1`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
date | today | date format '2015-07-22T12:16:06Z'
page | 1 | page number from the total pages returned in first page response


## Get a Specific Order

This endpoint retrieves a specific Order.

### HTTP Request

`GET /api/v2/order/<ID>`

If its a recurring order:

`GET /api/v2/order/<ID>/?date=<respective-date>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
date | today | date format '2015-07-22T12:16:06Z'
ID | None |The Order ID to retrieve


## Place an Order

This endpoint retrieves a specific Order.

### HTTP Request

`POST /api/v2/order/0/place_order/`

### POST Parameters
<ul>
  <li>"pickup_datetime":"2015-07-22T12:16:06Z"</li>
  <li>"customer_name":"shirish"</li>
  <li>"customer_phone_number":"9959026007"</li>
  <li>"is_reverse_pickup":false</li>
  <li>"notes":"sample notes" [Optional]</li>
  <li>"cod_amount":"220" [Optional]</li>
  <li>"total_cost":"220" [Optional]</li>
  <li>"vendor_order_id":"HS12453" [Optional]</li>
  <li>order_items:[{product_id: 1, quantity: 1}]</li> 
  <li>pickup_address:
    <ul>
      <li>"full_address":"604, Trade avenue, Suren road, Andheri East"</li>
      <li>"landmark":"WEH High Metro station" [Optional]</li> 
      <li>"pincode":"400099"</li>
    </ul>
  </li>
  <li>delivery_address:
    <ul>
      <li>"full_address":"604, Trade avenue, Suren road, Andheri East"</li>
      <li>"landmark":"WEH High Metro station" [Optional]</li> 
      <li>"pincode":"400099"</li>
    </ul>
  </li>
  <li>recurring: [Optional]
    <ul>
      <li>start_date:"2015-07-22T12:16:06Z"</li>
      <li>end_date:"2015-07-22T12:16:06Z"</li>
      <li>by_day:["MO","TU"]</li>
      <li>additional_dates:["2015-07-22T12:16:06Z","2015-07-22T12:16:06Z"] [Optional]</li>
    </ul>
  </li>  
</ul>


## Cancel Order

### HTTP Request

`POST /api/v2/order/<order-id>/cancel/`

### POST Parameters
For Recurring orders, please pass date parameter in post body
<ul>
  <li>"date":"2015-07-22T12:16:06Z" [Optional]</li>
</ul>  


### Order statuses
<ul>
  <li>ORDER_PLACED</li>
  <li>QUEUED</li>
  <li>REJECTED</li>
  <li>OUTFORPICKUP</li>
  <li>INTRANSIT</li>
  <li>OUTFORDELIVERY</li>
  <li>DELIVERED</li>
  <li>ATTEMPTED</li>
  <li>NOT_DELIVERED</li>
  <li>CANCELLED</li>
</ul>

# Customers

## Get All customers

This endpoint retrieves all customers.

### HTTP Request

`GET /api/v2/consumer/?page=1`

Parameter | Default | Description
--------- | ------- | -----------
page | 1 | page number from the total pages returned in first page response



## Get a Specific customer details

This endpoint retrieves a specific Order.

### HTTP Request

`GET /api/v2/consumer/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The Consumer ID to retrieve



# Products

## Get All products

This endpoint retrieves all products.

### HTTP Request

`GET /api/v2/product/`


## Add product

### HTTP Request

`POST /api/v2/product/`

### POST Parameters

<ul>
  <li>"name": Cake</li>
  <li>"description": Custom designed cakes</li>
  <li>"cost": 200 </li>
</ul>
