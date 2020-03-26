---
title: ETrak API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php

toc_footers:
  - <a href="https://etrak.io">Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the ETrak API Reference.


## Endpoints

Requests should be sent to:

Sandbox: `https://sandbox.api.etrak.io/api/{service}`
<br />
Production: `https://api.etrak.io/api/{service}`

## Accept Header

All requests to the ETrak API should include an `Accept` header:

```
Accept: application/json
```

## Version Header

All requests to the ETrak API should include a `version` header:

```
version: 1.0
```

## Content-type Header

All responses from the ETrak API have the header

```
Content-Type: application/json
```


## Authentication

ETrak uses API keys to allow access to the API. Your account manager can supply you with an API key.

ETrak expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: apikey`

Please contact your account manager to get an `apikey`

Example:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.etrak.io/api"
  -H "Authorization: apikey"
  -H "version: 1.0"
```

```php
<?php
// tbc
?>
```

> Make sure to replace `apikey` with your API key.

# Consignments

## Get A Consignment


```php
<?php
// tbc
?>
```

> Example JSON Response:

```json
{
    "id": "aab4fb51-9934-4529-8065-256cd297e456",
    "created": "2018-09-11 12:37:10",
    "modified": "2018-09-11 12:37:10",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_tracked",
    "barcode": "ETPML000000278",
    "client_ref1": "test",
    "client_ref2": "",
    "client_ref3": "",
    "batch": null,
    "overlabel_scan": null,
    "webhook": "https://www.yourwebsite.com/webhook",
    "export_type": "permanent",
    "reason_for_export": "sale",
    "status": "booked",
    "shipped": "N",
    "meta": {
    	"string_var1": "string1",
    	"bool_var1": true,
    	"int_var1": 0,
    	"float_var1": 0.0
    },
    "log": [
        {
            "message": "created",
            "time": "2019-01-21 10:16:19"
        },
        {
            "message": "Status change:  to book_onward_shipping",
            "time": "2019-01-21 10:16:19"
        }
    ],
    "address_delivery": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": "Leave with neighbour"
  	},
    "address_return": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": ""
    },
    "address_collection": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": ""
    },
    "pieces": [
        {
            "id": "46832880-db17-4b4b-a0c8-bd20ce6cf507",
            "weight": "1.00",
            "length": "30.00",
            "width": "6.00",
            "height": "5.00",
            "contents": [
                {
                    "description": "Book",
                    "value": "0.512",
                    "currency": "GBP",
                    "hs_code": "1122334455",
                    "quantity": "120",
                    "country_of_origin": "GB"
                }
            ],
            "checked_weight": "0.000",
            "log": null
        }
    ]
}
```


This method retrieves a single consignment.


### Endpoint

`GET https://api.etrak.io/api/Consignment/{id}`

URI Parameter | Description
--------- | -------
id | The ID of the consignment you wish to retrieve.

<aside class="success">
On success a 200 response code is sent.
</aside>








## Create A Consignment


```php
<?php


$data =
array (
  'contract_id' => '641b4b46-d0fe-4e76-b7e9-ce7754c26955',
  'service_id' => 'etrak_tracked',
  'barcode' => false,
  'client_ref1' => 'test',
  'client_ref2' => '',
  'client_ref3' => '',
  'batch' => '',
  'export_type' => 'permanent',
  'reason_for_export' => 'sale',
  'meta' => [],
  'webhook' => 'https://www.example.co.uk/webhook',
  'pieces' =>
  array (
    array (
      'weight' => '0.12',
      'length' => '1',
      'width' => '2',
      'height' => '3',
      'contents' =>
      array (
        array (
          'description' => 'book',
          'value' => '10.00',
          'currency' => 'GBP',
          'hs_code' => '1122334455',
          'quantity' => '120',
          'country_of_origin' => 'GB',
        ),
      ),
    ),
  ),
  'address_delivery' =>
  array (
    'name' => 'John Smith',
    'telephone' => '01234567890',
    'email' => 'john@example.com',
    'company' => 'ExampleCo',
    'line1' => 'Unit 1',
    'line2' => 'Example Street 2',
    'line3' => 'Exampletown',
    'city' => 'Example City',
    'state' => 'Examplecounty',
    'postcode' => 'AB1 1AB',
    'country' => 'GB',
    'district' => '',
    'notes' => '',
  ),
  'address_return' =>
  array (
    'name' => 'Reception',
    'telephone' => '+33 1 53 93 55 00',
    'email' => 'paris@marriot.com',
    'company' => 'Paris Marriott',
    'line1' => '70 Av. des Champs-Elysees',
    'line2' => '',
    'line3' => '',
    'city' => 'Paris',
    'state' => '',
    'postcode' => '75008',
    'country' => 'FR',
    'district' => '',
    'notes' => '',
  ),
  'address_collection' =>
  array (
    'name' => 'John Smith',
    'telephone' => '01234567890',
    'email' => 'john@example.com',
    'company' => 'ExampleCo',
    'line1' => 'Unit 1',
    'line2' => 'Example Street 2',
    'line3' => 'Exampletown',
    'city' => 'Example City',
    'state' => 'Examplecounty',
    'postcode' => 'AB1 1AB',
    'country' => 'GB',
    'district' => '',
    'notes' => '',
  ),
);

$etrak = \etrak\etrak::instance()->setApiKey('YOUR_API_KEY');
$r = \etrak\Consignment::create($data);
print_r($r);exit;

?>
```

> Example JSON Request:

```json
{
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_tracked",
    "barcode": false,
    "client_ref1": "test",
    "client_ref2": "",
    "client_ref3": "",
    "batch": "",
    "webhook": "https://www.yourwebsite.com/webhook",
    "export_type": "permanent",
    "reason_for_export": "sale",
    "meta": {
    	"string_var1": "string1",
    	"bool_var1": true,
    	"int_var1": 0,
    	"float_var1": 0.0
    },
    "pieces": [
        {
            "weight": "1.00",
            "length": "30.00",
            "width": "6.00",
            "height": "5.00",
            "contents": [
                {
                    "description": "Book",
                    "value": "0.512",
                    "currency": "GBP",
                    "hs_code": "1122334455",
                    "quantity": "120",
                    "country_of_origin": "GB"
                }
            ]
        }
    ],
  	"address_delivery": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": "Leave with neighbour"
  	},
    "address_return": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": ""
    },
    "address_collection": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": ""
    }
}
```

> Example JSON Response:

```json
{
    "id": "aab4fb51-9934-4529-8065-256cd297e456",
    "created": "2018-09-11 12:37:10",
    "modified": "2018-09-11 12:37:10",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_tracked",
    "barcode": "ETPML000000278",
    "client_ref1": "test",
    "client_ref2": "",
    "client_ref3": "",
    "batch": null,
    "overlabel_scan": null,
    "webhook": "https://www.yourwebsite.com/webhook",
    "export_type": "permanent",
    "reason_for_export": "sale",
    "status": "booked",
    "shipped": "N",
    "meta": {
    	"string_var1": "string1",
    	"bool_var1": true,
    	"int_var1": 0,
    	"float_var1": 0.0
    },
    "log": [
        {
            "message": "created",
            "time": "2019-01-21 10:16:19"
        },
        {
            "message": "Status change:  to book_onward_shipping",
            "time": "2019-01-21 10:16:19"
        }
    ],
    "address_delivery": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": "Leave with neighbour"
  	},
    "address_return": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": ""
    },
    "address_collection": {
    		"name": "John Smith",
    		"telephone": "01234567890",
    		"email": "john@example.com",
    		"company": "ExampleCo",
    		"line1": "Unit 1",
    		"line2": "Example Street 2",
    		"line3": "Exampletown",
    		"city": "Example City",
    		"state": "Examplecounty",
    		"postcode": "AB1 1AB",
    		"country": "GB",
    		"district": "",
            "notes": ""
    },
    "pieces": [
        {
            "id": "46832880-db17-4b4b-a0c8-bd20ce6cf507",
            "weight": "1.00",
            "length": "30.00",
            "width": "6.00",
            "height": "5.00",
            "contents": [
                {
                    "description": "Book",
                    "value": "0.512",
                    "currency": "GBP",
                    "hs_code": "1122334455",
                    "quantity": "120",
                    "country_of_origin": "GB"
                }
            ],
            "checked_weight": "0.000",
            "log": null
        }
    ]
}
```


This method creates a consignment.


### Endpoint

`POST https://api.etrak.io/api/Consignment`

### JSON Payload

Attribute | Description | Notes
--------- | ------- | -----------
contract_id | The contract to book on, get this from <a href="#list-all-contracts">listing contracts</a> | Mandatory
service_id | The service you want to use. | Mandatory
barcode | ETrak barcode | Specify your own (from your range) or "false" to be allocated one
client_ref1 | Your own reference | Optional
client_ref2 | Your own reference | Optional
client_ref3 | Your own reference | Optional
batch | Your own reference for a batch / dispatch of Consignments | Optional
webhook | URL we should post updates to | Optional
export_type | permanent or temporary | Optional
reason_for_export | sale, gift, intercompany transfer, sample, repair, return, personal items, other | Required if crossing customs union, else optional
pieces | Pieces in your consignment. Whilst the data format allows for multi-piece consignments, ETrak currently only supports single pieces | Mandatory
address_delivery | Where you want your parcel delivered to | Mandatory
address_collection | Where your parcel should be collected from (if appropriate) | Mandatory
address_return | Where you parcel should be returned to if there's a problem | Optional

<aside class="success">
On success a 201 response code is sent.
</aside>










## Cancel A Consignment


```php
<?php
// tbc
?>
```

This method cancels a consignment (if it is not already shipped).


### Endpoint

`DELETE https://api.etrak.io/api/Consignment/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the consignment you wish to cancel.

<aside class="success">
On success a 204 response code is sent.
</aside>









# Label

N.B. Labels belong to a `consignment`. They don't belong to `pieces`

## Get A Label


```php
<?php

$etrak = \etrak\etrak::instance()->setApiKey('YOUR_API_KEY');
$consignment_id = 'YOUR_CONSIGNMENT_ID';

$response = \etrak\Label::get($consignment_id);
header("Content-type:application/pdf");
header("Content-Disposition:inline;filename='$consignment_id.pdf");
echo base64_decode($response->body->data);


?>
```

> Example JSON Response:

```json
{
  "format" : "base64",
  "data" : "JVBERi0xLjcKJeLjz9MKNiAwIG9iago8PCAvVHlwZSAvUGFnZSAvUGFyZW5..."
}
```


This method retrieves a label for a single consignment.


### Endpoint

`GET https://api.etrak.io/api/Label/{id}/{format}`

URI Parameter | Description
------------- | -----------
id            | The ID of the consignment whose label you wish to retrieve.
format        | The format of the label, possible values are `inline` or `base64`

### Responses

Format | Description
------ | -----------
inline | Raw PDF data
base64 | JSON response with `data` property containing base64 encoded string of the PDF label

<aside class="success">
On success a 200 response code is sent.
</aside>













# Tracking

Tracking events belong to a consignment

## Get Tracking Events

```php
<?php

$etrak = \etrak\etrak::instance()->setApiKey('YOUR_API_KEY');
$barcode = 'ETXXX012345678';
$deliveryPostcode = 'SW1 1AA';

$response = \etrak\Track::getEvents($barcode, $deliveryPostcode);
// Events are in $response->body


?>
```

> Example JSON Response:

```json
[
    {
        "id": "2e37bf14-b55a-4320-9651-542c1b35f9fc",
        "consignment_id": "cfd52e8e-b593-4a90-bb5d-9c5483b4ce50",
        "happened_at": "2018-10-18 07:08:00",
        "message": "Item delivered",
        "harmonised_status": "DELIVERED__OTHER",
        "tracking_url": "https://onward.carrier.com/track?external_reference=123456789",
        "external_reference": "123456789",
        "location": "SOUTH AFRICA"
    },
    {
        "id": "a2766859-14b7-4a9b-8ed1-01a6d1d5a769",
        "consignment_id": "cfd52e8e-b593-4a90-bb5d-9c5483b4ce50",
        "happened_at": "2018-09-28 05:08:00",
        "message": "Scheduled for delivery but not completed - To be handeled",
        "harmonised_status": "UNKNOWN__HAS_MESSAGE_AND_LOCATION",
        "tracking_url": "https://onward.carrier.com/track?external_reference=123456789",
        "external_reference": "123456789",
        "location": "SOUTH AFRICA"
    },
    {
        "id": "a2393860-7848-4e3c-9109-628f0b5bb3bb",
        "consignment_id": "cfd52e8e-b593-4a90-bb5d-9c5483b4ce50",
        "happened_at": "2018-09-26 01:51:00",
        "message": "Departure to distribution network",
        "harmonised_status": "DEPARTED_FROM_FACILITY__HAS_LOCATION",
        "tracking_url": "https://onward.carrier.com/track?external_reference=123456789",
        "external_reference": "123456789",
        "location": "United Kingdom"
    }
]
```


This method retrieves an array of tracking events for the given consignment barcode and delivery postcode.


### Endpoint

`GET https://api.etrak.io/api/Track/{barcode}/{deliveryPostcode}`

URI Parameter | Description
--------- | ------- | -----------
barcode | The barcode of the consignment you wish to retrieve.
deliveryPostcode | The delivery postcode of the consignment you wish to retrieve.

<aside class="success">
On success a 200 response code is sent.
</aside>
