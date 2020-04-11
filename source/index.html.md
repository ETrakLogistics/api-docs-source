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
    "created_at": "2018-09-11 12:37:10",
    "updated_at": "2018-09-11 12:37:10",
    "status": "booked",
    "client_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_parcel_optimized",
    "barcode": "ETPML000000278",
    "client_ref1": "ABC0001",
    "client_ref2": "",
    "client_ref3": "",
    "batch": null,
    "webhook": null,
    "reason_for_export": "sale",
    "export_type": "permanent",
    "shipped": false,
    "meta": {
    	"string_var1": "string1",
    	"bool_var1": true,
    	"int_var1": 0,
    	"float_var1": 0.0
    },
    "address_collection": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": "Exampletown",
        "city": "Example City",
        "district": "",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": ""
    },
    "address_delivery": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": "Exampletown",
        "district": "",
        "city": "Example City",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": "Leave with neighbour"
  	},
    "address_return": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": "Exampletown",
        "district": "",
        "city": "Example City",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": ""
    },
    "pieces": [
        {
            "id": "a396b472-bfd0-45f8-96ae-10cbced1cee9",
            "weight": "1.000",
            "checked_weight": "0.000",
            "length": "30.0",
            "width": "6.0",
            "height": "5.0",
            "contents": [
                {
                    "description": "Book",
                    "value": "1.99",
                    "currency": "GBP",
                    "hs_code": "112233445566",
                    "quantity": "10",
                    "country_of_origin": "GB"
                }
            ]
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


$data = [
    'document_format' => 'pdf', // If you want the documents for the piece in the response, either include this, or add it as a query string parameter
    'contract_id' => '641b4b46-d0fe-4e76-b7e9-ce7754c26955',
    'service_id' => 'etrak_parcel_optimized',
    'client_ref1' => 'test',
    'client_ref2' => '',
    'client_ref3' => '',
    'webhook' => 'https://www.example.com/webhook',
    'reason_for_export' => 'sale',
    'export_type' => 'permanent',
    'meta' => null,
    'address_collection' => [
        'name' => 'John Smith',
        'company' => 'ExampleCo',
        'line1' => 'Unit 1',
        'line2' => 'Example Street 2',
        'line3' => '',
        'district' => '',
        'city' => 'Example City',
        'state' => 'Examplecounty',
        'postcode' => 'AB1 1AB',
        'country' => 'GB',
        'telephone' => '01234567890',
        'email' => 'john@example.com',
        'notes' => '',
    ],
    'address_delivery' => [
        'name' => 'Reception',
        'company' => 'Paris Marriott',
        'line1' => '70 Av. des Champs-Elysees',
        'line2' => '',
        'line3' => '',
        'district' => '',
        'city' => 'Paris',
        'state' => '',
        'postcode' => '75008',
        'country' => 'FR',
        'telephone' => '+33 1 53 93 55 00',
        'email' => 'paris@marriot.com',
        'notes' => '',
    ],
    'address_return' => [
        'name' => 'John Smith',
        'company' => 'ExampleCo',
        'line1' => 'Unit 1',
        'line2' => 'Example Street 2',
        'line3' => '',
        'district' => '',
        'city' => 'Example City',
        'state' => 'Examplecounty',
        'postcode' => 'AB1 1AB',
        'country' => 'GB',
        'telephone' => '01234567890',
        'email' => 'john@example.com',
        'notes' => '',
    ],
    'pieces' => [
        [
            'weight' => 1,
            'length' => 30,
            'width' => 20,
            'height' => 10,
            'contents' => [
                [
                    'description' => 'book',
                    'value' => 1.99,
                    'currency' => 'GBP',
                    'hs_code' => '112233445566',
                    'quantity' => 10,
                    'country_of_origin' => 'GB',
                ],
            ],
        ],
    ],
];

$etrak = \etrak\etrak::instance()->setApiKey('YOUR_API_KEY');
$r = \etrak\Consignment::create($data);
print_r($r);exit;

?>
```

> Example JSON Request:

```json
{
    "document_format": "pdf",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_parcel_optimized",
    "client_ref1": "test",
    "client_ref2": "",
    "client_ref3": "",
    "reason_for_export": "sale",
    "export_type": "permanent",
    "meta": null,
    "address_collection": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": "",
        "district": "",
        "city": "Example City",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": ""
    },
    "address_delivery": {
        "name": "Reception",
        "company": "Paris Marriott",
        "line1": "70 Av. des Champs-Elysees",
        "line2": "",
        "line3": "",
        "district": "",
        "city": "Paris",
        "state": "",
        "postcode": "75008",
        "country": "FR",
        "telephone": "+33 1 53 93 55 00",
        "email": "paris@marriot.com",
        "notes": ""
    },
    "address_return": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": "",
        "district": "",
        "city": "Example City",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": ""
    },
    "pieces": [
        {
            "weight": 1,
            "length": 30,
            "width": 20,
            "height": 10,
            "contents": [
                {
                    "description": "book",
                    "value": 1.99,
                    "currency": "GBP",
                    "hs_code": "112233445566",
                    "quantity": 10,
                    "country_of_origin": "GB"
                }
            ]
        }
    ]
}
```

> Example JSON Response:

```json
{
    "id": "a396b472-bfd0-45f8-96ae-10cbced1cee9",
    "created_at": "2020-03-26 15:00:10",
    "updated_at": "2020-03-26 15:00:10",
    "status": "booked",
    "client_id": "1dc00400-faef-4169-9691-ab7ad9f8f90c",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_parcel_optimized",
    "barcode": "ETPML000001536",
    "client_ref1": "test",
    "client_ref2": null,
    "client_ref3": null,
    "batch": null,
    "webhook": null,
    "reason_for_export": "sale",
    "export_type": "permanent",
    "shipped": false,
    "meta": null,
    "address_collection": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": null,
        "district": null,
        "city": "Example City",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": null
    },
    "address_delivery": {
        "name": "Reception",
        "company": "Paris Marriott",
        "line1": "70 Av. des Champs-Elysees",
        "line2": null,
        "line3": null,
        "district": null,
        "city": "Paris",
        "state": null,
        "postcode": "75008",
        "country": "FR",
        "telephone": "+33 1 53 93 55 00",
        "email": "paris@marriot.com",
        "notes": null
    },
    "address_return": {
        "name": "John Smith",
        "company": "ExampleCo",
        "line1": "Unit 1",
        "line2": "Example Street 2",
        "line3": null,
        "district": null,
        "city": "Example City",
        "state": "Examplecounty",
        "postcode": "AB1 1AB",
        "country": "GB",
        "telephone": "01234567890",
        "email": "john@example.com",
        "notes": null
    },
    "pieces": [
        {
            "id": "a396b472-bfd0-45f8-96ae-10cbced1cee9",
            "weight": "1.000",
            "checked_weight": "0.000",
            "length": "30.0",
            "width": "20.0",
            "height": "10.0",
            "contents": [
                {
                    "value": 1.99,
                    "hs_code": "112233445566",
                    "currency": "GBP",
                    "quantity": 10,
                    "description": "book",
                    "country_of_origin": "GB"
                }
            ],
            "documents": [
                {
                    "type": "label",
                    "format": "pdf",
                    "data": "JVBERi0xLjM..."
                },
                {
                    "type": "cn22",
                    "format": "pdf",
                    "data": "JVBERi0xLjQ..."
                }
            ]
        }
    ],
    "documents": [
        {
            "type": "commercial_invoice",
            "format": "pdf",
            "data": "JVBERi0xLjQ..."
        }
    ]
}
```


This method creates a consignment.

You can receive the label and any relevant customs documentation for a piece (or consignment) in the response, by including the `document_format` parameter in the request body, or as a querystring parameter in the URL.

Different onward services support different document formats, but currently, only PDF support is ubiquitous, so this is the only format recommended by ETrak at the moment.

If the consignment is crossing a customs union, and you have requested documents be included in the response, by including the `document_format` parameter, then the appropriate customs document, in PDF format, will also be included in the response for the piece (if the onward service is postal) or for the shipment (if the onward service is commercial).

If the onward service is a postal carrier, the type of document will be cn22 or cn23, and will be attached to the relevant piece, else it will be a proforma or commercial invoice, and will be attached to the consignment.

In the array of documents, each document indicates the type (`label|cn22|cn23|proforma_invoice|commercial_invoice`), the format (`pdf`), and the data contents, which are the base64 encoded PDF file.

### Endpoint

`POST https://api.etrak.io/api/Consignment`

Or if you want to include the documents in the response

`POST https://api.etrak.io/api/Consignment?document_format=pdf`



### JSON Payload

Attribute | Description | Notes
--------- | ------- | -----------
contract_id | The contract to book on, get this from your account manager | Mandatory
service_id | The service you want to use. | Mandatory
barcode | ETrak barcode | Specify your own (from your range, following our format) or omit the field to be allocated one
client_ref1 | Your own reference | Optional
client_ref2 | Your own reference | Optional
client_ref3 | Your own reference | Optional
batch | Your own reference for a batch / dispatch of Consignments | Optional
webhook | URL we should post updates to | Optional
reason_for_export | sale, gift, intercompany transfer, sample, repair, return, personal items, other | Required
export_type | permanent or temporary | Required
meta | Valid JSON data | Optional
address_collection | Where your parcel should be collected from (if appropriate) | Mandatory
address_delivery | Where you want your parcel delivered to | Mandatory
address_return | Where you parcel should be returned to if there's a problem | Optional
pieces | Pieces in your consignment. Whilst the data format allows for multi-piece consignments, ETrak currently only supports single pieces | Mandatory

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

N.B. Labels belong to a `piece` even though ETrak currently only supports single piece consignments.

Consequently, you can retrieve a label for the piece using the Consignment ID.

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
  "type" : "label",
  "format" : "pdf",
  "data" : "JVBERi0xLjcKJeLjz9MKNiAwIG9iago8PCAvVHlwZSAvUGFnZSAvUGFyZW5..."
}
```


This method retrieves a label for a consignment.


### Endpoint

`GET https://api.etrak.io/api/Label/{id}/{format}`

URI Parameter | Description
------------- | -----------
id            | The ID of the consignment whose label you wish to retrieve.
format        | The format of the label, possible values are `inline` or `base64`

### Responses

Format | Description
------ | -----------
inline | Raw PDF data with `Content-Type: application/pdf` and `Content-Disposition: inline; filename={barcode}.pdf` headers
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
        "for": "consignment",
        "consignment_id": "cfd52e8e-b593-4a90-bb5d-9c5483b4ce50",
        "piece_id": null,
        "happened_at": "2018-10-18 07:08:00",
        "happened_at_timezone": "unknown",
        "message": "Item delivered",
        "harmonised_status": "delivered",
        "sub_status": "signed for",
        "location": "New York",
        "country_code": "US",
        "extra": null
    },
    {
        "id": "2e37bf14-b55a-4320-9651-542c1b35f9fc",
        "for": "consignment",
        "consignment_id": "cfd52e8e-b593-4a90-bb5d-9c5483b4ce50",
        "piece_id": null,
        "happened_at": "2018-10-18 07:08:00",
        "happened_at_timezone": "unknown",
        "message": "Item delivered",
        "harmonised_status": "delivered",
        "sub_status": "signed for",
        "location": "New York",
        "country_code": "US",
        "extra": null
    },
    {
        "id": "2e37bf14-b55a-4320-9651-542c1b35f9fc",
        "for": "consignment",
        "consignment_id": "cfd52e8e-b593-4a90-bb5d-9c5483b4ce50",
        "piece_id": null,
        "happened_at": "2018-10-18 07:08:00",
        "happened_at_timezone": "unknown",
        "message": "Item delivered",
        "harmonised_status": "delivered",
        "sub_status": "signed for",
        "location": "New York",
        "country_code": "US",
        "extra": null
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
