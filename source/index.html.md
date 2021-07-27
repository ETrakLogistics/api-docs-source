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
    "reason_for_export": "sold",
    "export_type": "permanent",
    "terms_of_trade": "DDU",
    "shipping_charge" :  "3.99",
    "shipping_charge_currency" : "GBP",
    "tax" :  "3.99",
    "duty" : "3.99",
    "duties_and_taxes_chargeable_to_sender": true,
    "sender_tax_id": "",
    "sender_customs_id": "",
    "sender_ioss_number": "",
    "recipient_tax_id": "",
    "recipient_customs_id": "",
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
            ],
            "references": [
                {
                    "reference": "final mile tracking number for piece",
                    "type": "tracking_number"
                },
                {
                    "reference": "final mile label barcode value for piece",
                    "type": "barcode"
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
    'reason_for_export' => 'sold',
    'export_type' => 'permanent',
    'terms_of_trade' => 'DDU',
    'shipping_charge' => '3.99',
    'shipping_charge_currency' => 'GBP',
    'tax' => '3.99',
    'duty' => '3.99',
    'sender_tax_id' => '',
    'sender_customs_id' => '',
    'sender_ioss_number' => '',
    'recipient_tax_id' => '',
    'recipient_customs_id' => '',
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
    "reason_for_export": "sold",
    "export_type": "permanent",
    "terms_of_trade": "DDU",
    "shipping_charge" :  "3.99",
    "shipping_charge_currency" : "GBP",
    "tax" :  "3.99",
    "duty" : "3.99",
    "sender_tax_id": "",
    "sender_customs_id": "",
    "sender_ioss_number": "",
    "recipient_tax_id": "",
    "recipient_customs_id": "",
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
    "reason_for_export": "sold",
    "export_type": "permanent",
    "terms_of_trade": "DDU",
    "shipping_charge" :  "3.99",
    "shipping_charge_currency" : "GBP",
    "tax" :  "3.99",
    "duty" : "3.99",
    "duties_and_taxes_chargeable_to_sender": false,
    "sender_tax_id": "",
    "sender_customs_id": "",
    "sender_ioss_number": "",
    "recipient_tax_id": "",
    "recipient_customs_id": "",
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
            ],
            "references": [
                {
                    "reference": "final mile tracking number for piece",
                    "type": "tracking_number"
                },
                {
                    "reference": "final mile label barcode value for piece",
                    "type": "barcode"
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
    ],
    "references": [
        {
            "reference": "final mile tracking number for shipment",
            "type": "tracking_number"
        },
        {
            "reference": "final mile label barcode value for shipment",
            "type": "barcode"
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

Each piece and the consignment can also have zero or more references, such as the tracking number from the final mile carrier.

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
reason_for_export | sold (formerly "sale"), gift, documents, intra company transfer (formerly "intercompany transfer"), sample, repair, returned (formerly "return"), personal items, temporary export, other | Required
export_type | permanent or temporary | Required
terms_of_trade | DDU or DDP | Optional. If omitted DDU is assumed
shipping_charge | The amount charged by the vendor of the products being shipped, to the final customer of the products for shipping them, i.e. the shippings costs in an ecommerce order | Should be a number, up to 2 decimal places, e.g. 3.99. Mandatory for DDP (because it's part of the Duties & Tax calculation) although if not supplied 0.00, in the `shipping_charge_currency` is assumed
shipping_charge_currency | The currency of the `shipping_charge` | 3 character ISO currency code, e.g. GBP or EUR or USD. Mandatory if `shipping_charge` is provided. Should be the same as the currency of the declared value in the piece contents
tax | The total tax paid for DDP shipments (for products, shipping, insurance etc) | Should be a number, up to 2 decimal places, e.g. `3.99`. Currency is the currency of the declared value in the piece contents. Optional, if omitted, and `terms_of_trade` is DDP, we will calculate it for you
duty | The total duty paid for DDP shipments (for products, shipping, insurance etc) | Should be a number, up to 2 decimal places, e.g. `3.99`. Currency is the currency of the declared value in the piece contents. Optional, if omitted, and `terms_of_trade` is DDP, we will calculate it for you
duties_and_taxes_chargeable_to_sender | Bool. Should not be supplied in request. It will be in the response though. We determine the value based on terms_of_trade (DDP), and whether IOSS eligible (Non EU > EU, goods intrinsic value < 150EUR or 135GBP & sender_ioss_number supplied) | Omit
sender_tax_id | VAT No | Optional
sender_customs_id | EORI No | Optional
sender_ioss_number | IOSS Number | Optional
recipient_tax_id | VAT No | Optional
recipient_customs_id | EORI No | Optional
meta | Valid JSON data | Optional
address_collection | Where your parcel should be collected from (if appropriate) | Mandatory
address_delivery | Where you want your parcel delivered to | Mandatory
address_return | Where you parcel should be returned to if there's a problem | Optional
pieces | Pieces in your consignment. Whilst the data format allows for multi-piece consignments, ETrak currently only supports single pieces | Mandatory

#### Piece

Attribute | Description | Notes
--------- | ------- | -----------
weight | The weight of the piece | Float in kilograms
length | The length of the piece | Float in centimeters
width | The width of the piece | Float in centimeters
height | The height of the piece | Float in centimeters
contents | The contents of the piece | An array of objects

#### Contents

Attribute | Description | Notes
--------- | ------- | -----------
value | The value of the item | Float, in the currency listed below
hs_code | The hs_code of the item | Between 6 and 12, digits only
currency | The currency of the item | 3-letter ISO code
quantity | The quantity of the item | Integer, min 1
description | The description of the item | String, max 255 chars
country_of_origin | The country_of_origin of the item | 2-letter ISO code

#### Address

Attribute | Description | Notes
--------- | ------- | -----------
name | The name of the address | String
company | The company of the address | String
line1 | The line1 of the address | String
line2 | The line2 of the address | String
line3 | The line3 of the address | String
district | The district of the address | String
city | The city of the address | String
state | The state of the address | String
postcode | The postcode of the address | String
country | The country of the address | String
telephone | The telephone of the address | String
email | The email of the address | String
notes | The notes of the address | String

<aside class="success">
On success a 201 response code is sent.
</aside>







## Update A Consignment



> Example JSON Request:

```json
{
    "service_id": "ontrak"
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
    "service_id": "ontrak",
    "barcode": "ETPML000001536",
    "client_ref1": "test",
    "client_ref2": null,
    "client_ref3": null,
    "batch": null,
    "webhook": null,
    "reason_for_export": "sold",
    "export_type": "permanent",
    "terms_of_trade": "DDU",
    "shipping_charge" :  "3.99",
    "shipping_charge_currency" : "GBP",
    "tax" :  "3.99",
    "duty" : "3.99",
    "duties_and_taxes_chargeable_to_sender": false,
    "sender_tax_id": "",
    "sender_customs_id": "",
    "sender_ioss_number": "",
    "recipient_tax_id": "",
    "recipient_customs_id": "",
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
            ],
            "references": [
                {
                    "reference": "final mile tracking number for piece",
                    "type": "tracking_number"
                },
                {
                    "reference": "final mile label barcode value for piece",
                    "type": "barcode"
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
    ],
    "references": [
        {
            "reference": "final mile tracking number for consignment",
            "type": "tracking_number"
        },
        {
            "reference": "final mile label barcode value for consignment",
            "type": "barcode"
        }
    ]
}
```


This method updates a consignment. You can use it to change the service that a consignment is booked on. E.g. from `epak` to `ontrak`

You will always receive a new label and any other relevant customs documentation, and new onward carrier references for a piece (or consignment) in the response.

### Endpoint

`PATCH https://api.etrak.io/api/Consignment/{id}`


URI Parameter | Description
--------- | ------- | -----------
id | The ID of the consignment you wish to update.



<aside class="success">
On success a 200 response code is sent.
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






# Piece



## Update A Piece



> Example JSON Request:

```json
{
    "checked_weight": 1.907,
    "checked_length": 60,
    "checked_width": 29,
    "checked_height": 1
}
```

> Example JSON Response:

```json
{
    "data": {
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
        "consignment": {
            "id": "a396b472-bfd0-45f8-96ae-10cbced1cee9",
            "created_at": "2020-03-26 15:00:10",
            "updated_at": "2020-03-26 15:00:10",
            "status": "booked",
            "client_id": "1dc00400-faef-4169-9691-ab7ad9f8f90c",
            "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
            "service_id": "ontrak",
            "barcode": "ETPML000001536",
            "client_ref1": "test",
            "client_ref2": null,
            "client_ref3": null,
            "batch": null,
            "webhook": null,
            "reason_for_export": "sold",
            "export_type": "permanent",
            "terms_of_trade": "DDU",
            "shipping_charge" :  "3.99",
            "shipping_charge_currency" : "GBP",
            "tax" :  "3.99",
            "duty" : "3.99",
            "duties_and_taxes_chargeable_to_sender": false,
            "sender_tax_id": "",
            "sender_customs_id": "",
            "sender_ioss_number": "",
            "recipient_tax_id": "",
            "recipient_customs_id": "",
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
                    ],
                    "references": [
                        {
                            "reference": "final mile carrier tracking number for piece",
                            "type": "tracking_number"
                        },
                        {
                            "reference": "final mile label barcode for piece",
                            "type": "barcode"
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
            ],
            "references": [
                {
                    "reference": "final mile tracking number for piece",
                    "type": "tracking_number"
                },
                {
                    "reference": "final mile label barcode value for piece",
                    "type": "barcode"
                }
            ]
        }
    },
    "message": "Checked weight/dimensions are within latest defined weight/dimensions."
}
```


This method updates a piece. You can use it to set the checked_weight and checked dimensions properties of a piece.

There are 2 types of successful responses, which you get depends on whether the checked weight and dimensions are less than or equal to the declared, or greater than declared, but still within the parameters of the booked service.

### Endpoint

`PATCH https://api.etrak.io/api/pieces/{id}`


URI Parameter | Description
--------- | ------- | -----------
id | The ID of the Piece you wish to update.



<aside class="success">
A 200 response code is sent if the checked weight and dimensions are less than or equal to the declared.

The response body contains a data property that echoes back the properties of the piece.

You'll also get a messsage property with a value such as "Checked weight/dimensions are within latest defined weight/dimensions."
</aside>

<aside class="success">
A 201 response code is sent if the checked weight and dimensions are more than the declared, but still within the parameters for the original service booked.

The response body contains a data property that echoes back the properties of the piece, and a consignment property that echoes back the properties of the consignment, including it's addresses and all it's pieces, and new labels and possibly customs docs, and onward carrier references.

You'll also get a message such as "Checked weight/dimensions are NOT within latest defined weight/dimensions, but are within limits of booked service. 1 new weight/dimension exceeds original: The weight was originally 1.906, but is now 1.907. Consignment has been automatically rebooked with the onward carrier. See data in response for new documents and references."
</aside>

<aside class="danger">
A 422 response code is sent if the checked weight and dimensions are more than the declared, and greater the maximum parameters for the original service booked. In this case, you should update the service_id on the consignment.


</aside>




# Tracking

Please note we also support webhook / callback for pushing new events to your system as soon as we receive them, or can create text files containing all new events received since the last file was produced, every hour, and put them on an SFTP server we can provide you with access to. Get in touch with your account manager for more info.

We also have our public facing tracking page at https://track.etrak.io/{barcode}

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


# Available Services Checks

You can check what services are available for consignment before you book it, by POSTing the consignment data in the same format as the payload for creating it.

## Get Available Services

> Example JSON Request:

```json
{
  "contract_id": "Insert Your Contract ID Here",
  "terms_of_trade": "DDP",
  "sender_ioss_number": "IM1234567890",
  "address_collection": {
    "postcode": "SO53 3TG",
    "country": "GB"
  },
  "address_delivery": {
    "postcode":"75000",
    "country":"FR"
  },
  "pieces": [
    {
      "weight": "1.00",
      "length": "30.00",
      "width": "6.00",
      "height": "5.00",
      "contents": [
        {
          "value": "0.99",
          "currency": "GBP",
          "quantity": "10"
        }
      ]
    }
  ]
}
```

> Example JSON Response:

```json
[
  {
    "name": "EPak",
    "code": "epak",
    "aliases": [
      "alias 1",
      "alias 2"
    ],
    "volumetric_divisor": 5000
  },
  {
    "name": "OnTrak",
    "code": "ontrak",
    "aliases": null,
    "volumetric_divisor": 5000
  }
]
```

> Example JSON Error Response:

```json
{
  "message": "The given data was invalid.",
  "errors": {
    "contract_id": [
      "The contract id field is required."
    ]
  }
}
```

### Endpoint

`POST https://api.etrak.io/api/available-services-checks`

### JSON Payload

Attribute | Description | Notes
--------- | ------- | -----------
contract_id | The contract to check available services for, get this from your account manager | Mandatory
terms_of_trade | The terms of trade you want to use. Valid values are DDP or DDU. If omitted, DDU is assumed | Optional
sender_ioss_number | The sender's IOSS number. This is required for the consignment to be considered IOSS eligible, and if all other IOSS requirements are met (lane, intrinsic value), each service in the response can be used for IOSS. If supplied, should be a valid IOSS number. | Optional
address_collection.postcode | The 'from' address postcode. This is used in conjunction with the from address country to determine the customs jurisdiction and is part of the checks to see whether the consignment is IOSS eligible. | Optional
address_collection.country | The 'from' address country. | Mandatory
address_delivery.postcode | The 'to' address postcode. This is used in conjunction with the to address country to determine the customs jurisdiction and is part of the checks to see whether the consignment is IOSS eligible. | Optional
address_delivery.country | The 'to' address country. | Mandatory
pieces | Array of pieces. Currently only single piece consignments are supported. | Mandatory
pieces.*.weight | Float. The weight of the piece in kilograms. Up to 3 decimal places are supported | Mandatory
pieces.*.length | Float. The length of the piece in centimeters. Up to 2 decimal places are supported | Mandatory
pieces.*.width | Float. The width of the piece in centimeters. Up to 2 decimal places are supported | Mandatory
pieces.*.height | Float. The height of the piece in centimeters. Up to 2 decimal places are supported | Mandatory
pieces.*.contents | Array of contents within the piece. The `value`, `quantity` and `currency` properties within each item are used to determine the intrinsic value of the consignment to see if it's IOSS eligible, if the other criteria for IOSS are met. | Optional
pieces.*.contents.*.value | Float. The unit value of the item in the item's `currency`. Up to 2 decimal places are supported. See description for `pieces.*.contents` about why this may be supplied | Optional
pieces.*.contents.*.currency | String. 3 Characters. The ISO currency code, e.g. GBP, that the unit `value` is in. See description for `pieces.*.contents` about why this may be supplied | Optional
pieces.*.contents.*.quantity | Integer. The number of unit of this item in the piece. The unit `value` of the item is multiplied by this to determine the intrinsic value when checking for IOSS eligibility. See description for `pieces.*.contents` about why this may be supplied | Optional

<aside class="success">
On success a 200 response code is sent.
The response body contains an array of services that a consignment with these properties could be booked on.
If there are no available services, then the response body will contain an empty array
</aside>

<aside class="warning">
If the request payload is invalid, a 422 response code is sent, along with a body containing the errors.
</aside>
