---
title: eTrak API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php

toc_footers:
  - <a href="https://etrak.io">Sign Up for a Developer Key</a>
  
includes:
  - errors

search: true
---



# Introduction

Welcome to the eTrak API Reference.


## Endpoints

If you don't wish to use the PHP SDK, your requests should be sent to:

Sandbox: `https://sandbox.api.etrak.io/api/{service}`
<br />
Production: `https://api.etrak.io/api/{service}`




## Sandbox

eTrak has a Sandbox environment that mirrors the production environment for testing.

The PHP SDK also supports the Sandbox (see the docs for details).


## PHP SDK

There's a PHP SDK available for this API. You can get it here: <br />
<a href="https://github.com/ParcelMonkeyGroup/etrak-php">https://github.com/ParcelMonkeyGroup/etrak-php</a>.


# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.etrak.io/api"
  -H "Authorization: apikey"
```

```php
<?
// tbc
?>
```

> Make sure to replace `apikey` with your API key.

eTrak uses API keys to allow access to the API. You can create an eTrak API key at [eTrak.io](https://etrak.io).

eTrak expects for the API key to be included in all API requests (except the `AuthenticateUser` service) to the server in a header that looks like the following:

`Authorization: apikey`

<aside class="notice">
You must replace <code>apikey</code> with your personal API key.
</aside>









## AuthenticateUser


```php
<?

$etrak = \etrak\etrak::instance();
$r = \etrak\AuthenticateUser::create([
  'email' => 'rich@parcelmonkey.com',
  'password' => 'hello1'
]);
print_r($r);

?>
```


> Example JSON Request Body:

```json
{
  "email": "rich@parcelmonkey.com",
  "password": "pa55word"
}
```

> Example JSON Response:

```json
{
    "apikey": "5DFB8-16EF2-E5358-0E24F-E37AA-6FBA1",
    "expires": "2018-03-28 19:09:46"
}
```



This method generates a <strong>temporary</strong> API key (that expires in 60 minutes) by providing your eTrak.io `email` and `password`.  You can then use this API key in a subsequent request to the `CreateApiKey` service to obtain a more permanent API key.

<aside class="notice">
  You do not have to use the API to create keys. You can do this by logging into your account at eTrak.io
</aside>

<aside class="warning">
  You should not use this to authenticate your application - it exists solely for the purpose of generating a <strong>temporary</strong> key so that you might then generate a permanent one using the <strong>`CreateApiKey`</strong> service. The reason for this is that this method relies on your email and password that could change at a later date.
</aside>

### Endpoint

`POST https://etrak.io/api/AuthenticateUser`

### JSON Payload

Attribute | Mandatory | Description
--------- | ------- | -------------------
email | true | Your eTrak.io login email.
password | true | Your eTrak.io password.

<aside class="success">
  You can now use the API key returned in subsequent requests to the API for 60 minutes.
</aside>


<aside class="success">
On success a 200 response code is sent.
</aside>







## CreateApiKey


```php
<?

$etrak = \etrak\etrak::instance()->setApiKey(YOUR_TEMPORARY_API_KEY);
$r = \etrak\ApiKey::create([
  'reference' => 'reference for this API key'
]);
print_r($r);

?>
```


> Example JSON Request Body:

```json
{
	"reference": "my application"
}
```

> Example JSON Response:

```json
{
    "apikey": "1467B-B0083-1C615-7C3A8-B0B89-B77C1",
    "expires": "2118-03-27 19:01:30"
}
```


This method generates a new API key (that expires in 100 years) by providing another eTrak.io API key (for example a temporary one created with `AuthenticateUser`).

<aside class="notice">
  You do not have to use the API to create keys. You can do this by logging into your account at eTrak.io
</aside>

### Endpoint

`POST https://etrak.io/api/CreateApiKey`

### JSON Payload

Attribute | Mandatory | Description
--------- | ------- | -------------------
reference | true | A free text reference for this API key.

<aside class="success">
  You can use this API in subsequent requests to the API.
</aside>


<aside class="success">
On success a 201 response code is sent.
</aside>








# Users

Users are people who can log in and manage your eTrak.io account.

<aside class="notice">
  You can manage users from your eTrak.io account online too.
</aside>

## List All Users


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
[
    {
        "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
        "created": "2018-03-27 16:17:30",
        "modified": "2018-03-27 16:17:30",
        "email": "rich@parcelmonkey.com",
        "name": "Richard Barrett"
    }
]
```


This method lists all users registered on your eTrak.io account.


### Endpoint

`GET https://etrak.io/api/Users`

<aside class="success">
On success a 200 response code is sent.
</aside>








## Get A User


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 16:17:30",
    "modified": "2018-03-27 16:17:30",
    "email": "rich@parcelmonkey.com",
    "name": "Richard Barrett"
}
```


This method retrieves a single user registered on your eTrak.io account.


### Endpoint

`GET https://etrak.io/api/User/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the user you wish to retrieve.



<aside class="success">
On success a 200 response code is sent.
</aside>





## Create A User


```php
<?
// tbc
?>
```

> Example JSON Request:

```json
{
    "email": "rich1@parcelmonkey.com",
    "password": "hello1",
    "name": "Rich Barrett"
}
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 20:31:43",
    "modified": "2018-03-27 20:31:43",
    "email": "rich3@parcelmonkey.com",
    "name": "Rich Barrett"
}
```


This method creates a user. Any field you specify in the JSON payload will be updated.


### Endpoint

`POST https://etrak.io/api/User`

### JSON Payload

Attribute | Description
--------- | ------- | -----------
email | Set the user's email.
password | Set the user's password.
name | Set the user's name.


<aside class="success">
On success a 201 response code is sent.
</aside>








## Update A User


```php
<?
// tbc
?>
```

> Example JSON Request:

```json
{
    "email": "rich@parcelmonkey.com",
    "password": "hello1",
    "name": "Rich Barrett"
}
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 16:17:30",
    "modified": "2018-03-27 20:17:30",
    "email": "rich@parcelmonkey.com",
    "name": "Rich Barrett"
}
```


This method updates a user. Any field you specify in the JSON payload will be updated.


### Endpoint

`PUT https://etrak.io/api/User/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the user you wish to retrieve.

### JSON Payload

Attribute | Description
--------- | ------- | -----------
email | Update the user's email.
password | Update the user's password.
name | Update the user's name.


<aside class="success">
On success a 200 response code is sent.
</aside>





## Delete A User


```php
<?
// tbc
?>
```

This method deletes a user from your eTrak.io account.


### Endpoint

`DELETE https://etrak.io/api/User/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the user you wish to delete.

<aside class="success">
On success a 204 response code is sent.
</aside>
















# Account


## Get Your Account Info


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 16:04:58",
    "modified": "2018-03-27 21:10:23",
    "name": "Parcel Monkey UK",
    "company": "Parcel Monkey Ltd",
    "address1": "Unit 21",
    "address2": "East Links",
    "address3": "Tollgate",
    "town": "Chandlers Ford",
    "county": "Hampshire",
    "postcode": "SO53 3TG",
    "country": "GB"
}
```

This method retrieves your eTrak.io account details.


### Endpoint

`GET https://etrak.io/api/Account`


<aside class="success">
On success a 200 response code is sent.
</aside>






## Update Your Account


```php
<?
// tbc
?>
```

> Example JSON Request:

```json
{
    "address1": "Unit 21",
    "address2": "East Links",
    "address3": "Tollgate",
    "town": "Chandlers Ford",
    "county": "Hampshire",
    "postcode": "SO53 3TG",
    "country": "GB"
}
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 16:04:58",
    "modified": "2018-03-27 21:10:23",
    "name": "Parcel Monkey UK",
    "company": "Parcel Monkey Ltd",
    "address1": "Unit 21",
    "address2": "East Links",
    "address3": "Tollgate",
    "town": "Chandlers Ford",
    "county": "Hampshire",
    "postcode": "SO53 3TG",
    "country": "GB"
}
```


This method updates your account details. Any field you specify in the JSON payload will be updated.


### Endpoint

`PUT https://etrak.io/api/Account`


### JSON Payload

Attribute | Description
--------- | ------- | -----------
address1 | Update your invoicing address.
address2 | Update your invoicing address.
address3 | Update your invoicing address.
town | Update your invoicing address.
county | Update your invoicing address.
postcode | Update your invoicing address.
country | Update your invoicing address.

<aside class="success">
On success a 200 response code is sent.
</aside>

























# Contracts

Contracts represent the commercial agreements you have with eTrak.

## List All Contracts


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
[
    {
        "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
        "created": "2018-03-27 16:34:02",
        "modified": "2018-03-27 16:34:02",
        "name": "initial contract",
        "status": "active"
    },
    {
        "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
        "created": "2018-03-27 16:47:20",
        "modified": "2018-03-27 16:47:20",
        "name": "second contract",
        "status": "active"
    }
]
```

This method lists all contracts on your eTrak.io account.


### Endpoint

`GET https://etrak.io/api/Contracts`


<aside class="success">
On success a 200 response code is sent.
</aside>







## Get A Contract


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 16:34:02",
    "modified": "2018-03-27 16:34:02",
    "name": "initial contract",
    "status": "active"
}
```


This method retrieves a single contract on your eTrak.io account.


### Endpoint

`GET https://etrak.io/api/Contract/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the contract you wish to retrieve.


<aside class="success">
On success a 200 response code is sent.
</aside>








# Users

Users are people who can log in and manage your eTrak.io account.

<aside class="notice">
  You can manage users from your eTrak.io account online too.
</aside>

## List All Users


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
[
    {
        "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
        "created": "2018-03-27 16:17:30",
        "modified": "2018-03-27 16:17:30",
        "email": "rich@parcelmonkey.com",
        "name": "Richard Barrett"
    }
]
```


This method lists all users registered on your eTrak.io account.


### Endpoint

`GET https://etrak.io/api/Users`

<aside class="success">
On success a 200 response code is sent.
</aside>








## Get A User


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
{
    "id": "c87ea71e-e03b-4d9f-94aa-13ba91b50eea",
    "created": "2018-03-27 16:17:30",
    "modified": "2018-03-27 16:17:30",
    "email": "rich@parcelmonkey.com",
    "name": "Richard Barrett"
}
```


This method retrieves a single user registered on your eTrak.io account.


### Endpoint

`GET https://etrak.io/api/User/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the user you wish to retrieve.

<aside class="success">
On success a 200 response code is sent.
</aside>












# Consignments

## Get A Consignment


```php
<?
// tbc
?>
```

> Example JSON Response:

```json
{
    "id": "3260bbf8-e2f4-4a78-b719-e11c17d881f2",
    "created": "2018-05-11 11:38:38",
    "modified": "2018-05-11 11:38:38",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_tracked",
    "barcode": "ETYCL000000041",
    "client_ref1": "richjohntest",
    "client_ref2": "",
    "client_ref3": "",
    "webhook": "https://www.parcelmonkey.co.uk/webhook",
    "address_delivery": {
        "name": "Richard Barrett",
        "company": "Parcel Monkey",
        "telephone": "01234567890",
        "email": "rich@parcelmonkey.com",
        "line1": "Unit 21",
        "line2": "Tollgate",
        "line3": "Eastleigh",
        "city": "Chandlers Ford",
        "state": "Hampshire",
        "postcode": "SO53 3TG",
        "country": "GB",
        "district": ""
    },
    "address_collection": {
        "name": "Richard Barrett",
        "company": "Parcel Monkey",
        "telephone": "01234567890",
        "email": "rich@parcelmonkey.com",
        "line1": "Unit 21",
        "line2": "Tollgate",
        "line3": "Eastleigh",
        "city": "Chandlers Ford",
        "state": "Hampshire",
        "postcode": "SO53 3TG",
        "country": "GB",
        "district": ""
    },
    "address_return": {
        "name": "Richard Barrett",
        "company": "Parcel Monkey",
        "telephone": "01234567890",
        "email": "rich@parcelmonkey.com",
        "line1": "Unit 21",
        "line2": "Tollgate",
        "line3": "Eastleigh",
        "city": "Chandlers Ford",
        "state": "Hampshire",
        "postcode": "SO53 3TG",
        "country": "GB",
        "district": ""
    }
}
```


This method retrieves a single consignment.


### Endpoint

`GET https://etrak.io/api/Consignment/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the consignment you wish to retrieve.

<aside class="success">
On success a 200 response code is sent.
</aside>








## Create A Consignment


```php
<?


$data = 
array (
  'contract_id' => '641b4b46-d0fe-4e76-b7e9-ce7754c26955',
  'service_id' => 'etrak_tracked',
  'barcode' => false,
  'client_ref1' => 'test',
  'client_ref2' => '',
  'client_ref3' => '',
  'webhook' => 'https://www.parcelmonkey.co.uk/webhook',
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
        ),
      ),
    ),
  ),
  'address_delivery' => 
  array (
    'name' => 'Richard Barrett',
    'telephone' => '01234567890',
    'email' => 'rich@parcelmonkey.com',
    'company' => 'Parcel Monkey',
    'line1' => 'Unit 21',
    'line2' => 'Tollgate',
    'line3' => 'Eastleigh',
    'city' => 'Chandlers Ford',
    'state' => 'Hampshire',
    'postcode' => 'SO53 3TG',
    'country' => 'GB',
    'district' => '',
  ),
  'address_return' => 
  array (
    'name' => 'Richard Barrett',
    'telephone' => '01234567890',
    'email' => 'rich@parcelmonkey.com',
    'company' => 'Parcel Monkey',
    'line1' => 'Unit 21',
    'line2' => 'Tollgate',
    'line3' => 'Eastleigh',
    'city' => 'Chandlers Ford',
    'state' => 'Hampshire',
    'postcode' => 'SO53 3TG',
    'country' => 'GB',
    'district' => '',
  ),
  'address_collection' => 
  array (
    'name' => 'Richard Barrett',
    'telephone' => '01234567890',
    'email' => 'rich@parcelmonkey.com',
    'company' => 'Parcel Monkey',
    'line1' => 'Unit 21',
    'line2' => 'Tollgate',
    'line3' => 'Eastleigh',
    'city' => 'Chandlers Ford',
    'state' => 'Hampshire',
    'postcode' => 'SO53 3TG',
    'country' => 'GB',
    'district' => '',
  ),
);

$etrak = \etrak\etrak::instance()->setApiKey(YOUR_API_KEY);
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
	"client_ref1": "richjohntest",
	"client_ref2": "",
	"client_ref3": "",
	"webhook": "https://www.parcelmonkey.co.uk/webhook",
	"pieces": [
		{
			"weight":"0.12",
			"length": "1",
			"width": "2",
			"height": "3",
			"contents": [
				{
					"description": "book",
					"value" : "10.00",
					"currency" : "GBP",
					"hs_code": "1122334455"
				}
			]
		}
	],
	"address_delivery": {
		"name": "Richard Barrett",
		"telephone": "01234567890",
		"email": "rich@parcelmonkey.com",
		"company": "Parcel Monkey",
		"line1": "Unit 21",
		"line2": "Tollgate",
		"line3": "Eastleigh",
		"city": "Chandlers Ford",
		"state": "Hampshire",
		"postcode": "SO53 3TG",
		"country": "GB",
		"district": ""
	},
	"address_return": {
		"name": "Richard Barrett",
		"telephone": "01234567890",
		"email": "rich@parcelmonkey.com",
		"company": "Parcel Monkey",
		"line1": "Unit 21",
		"line2": "Tollgate",
		"line3": "Eastleigh",
		"city": "Chandlers Ford",
		"state": "Hampshire",
		"postcode": "SO53 3TG",
		"country": "GB",
		"district": ""
	},
	"address_collection": {
		"name": "Richard Barrett",
		"telephone": "01234567890",
		"email": "rich@parcelmonkey.com",
		"company": "Parcel Monkey",
		"line1": "Unit 21",
		"line2": "Tollgate",
		"line3": "Eastleigh",
		"city": "Chandlers Ford",
		"state": "Hampshire",
		"postcode": "SO53 3TG",
		"country": "GB",
		"district": ""
	}
}
```

> Example JSON Response:

```json
{
    "id": "3260bbf8-e2f4-4a78-b719-e11c17d881f2",
    "created": "2018-05-11 11:38:38",
    "modified": "2018-05-11 11:38:38",
    "contract_id": "641b4b46-d0fe-4e76-b7e9-ce7754c26955",
    "service_id": "etrak_tracked",
    "barcode": "ETYCL000000041",
    "client_ref1": "richjohntest",
    "client_ref2": "",
    "client_ref3": "",
    "webhook": "https://www.parcelmonkey.co.uk/webhook",
    "address_delivery": {
        "name": "Richard Barrett",
        "company": "Parcel Monkey",
        "telephone": "01234567890",
        "email": "rich@parcelmonkey.com",
        "line1": "Unit 21",
        "line2": "Tollgate",
        "line3": "Eastleigh",
        "city": "Chandlers Ford",
        "state": "Hampshire",
        "postcode": "SO53 3TG",
        "country": "GB",
        "district": ""
    },
    "address_collection": {
        "name": "Richard Barrett",
        "company": "Parcel Monkey",
        "telephone": "01234567890",
        "email": "rich@parcelmonkey.com",
        "line1": "Unit 21",
        "line2": "Tollgate",
        "line3": "Eastleigh",
        "city": "Chandlers Ford",
        "state": "Hampshire",
        "postcode": "SO53 3TG",
        "country": "GB",
        "district": ""
    },
    "address_return": {
        "name": "Richard Barrett",
        "company": "Parcel Monkey",
        "telephone": "01234567890",
        "email": "rich@parcelmonkey.com",
        "line1": "Unit 21",
        "line2": "Tollgate",
        "line3": "Eastleigh",
        "city": "Chandlers Ford",
        "state": "Hampshire",
        "postcode": "SO53 3TG",
        "country": "GB",
        "district": ""
    }
}
```


This method creates a consignment.


### Endpoint

`POST https://etrak.io/api/Consignment`

### JSON Payload

Attribute | Description | Notes
--------- | ------- | -----------
contract_id | The contract to book on
service_id | The service you want to use.
barcode | eTrak barcode | Specify your own (from your range) or "false" to be allocated one
client_ref1 | Your own reference | Optional
client_ref2 | Your own reference | Optional
client_ref3 | Your own reference | Optional
webhook | URL we should post updates to | Optional
pieces | Pieces in your consignment |
address_delivery | Where you want your parcel delivered to
address_collection | Where your parcel should be collected from (if appropriate)
address_return | Where you parcel should be returned to if there's a problem


<aside class="success">
On success a 201 response code is sent.
</aside>










## Cancel A Consignment


```php
<?
// tbc
?>
```

This method cancels a consignment (if it is not already shipped).


### Endpoint

`DELETE https://etrak.io/api/Consignment/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the consignment you wish to cancel.

<aside class="success">
On success a 204 response code is sent.
</aside>









# Label

Labels belong to a consignment.

## Get A Label


```php
<?

$etrak = \etrak\etrak::instance()->setApiKey(YOUR_API_KEY);
$consignment_id = YOUR_CONSIGNMENT_ID;

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


This method retrieves a single consignment.


### Endpoint

`GET https://etrak.io/api/Label/{id}`

URI Parameter | Description
--------- | ------- | -----------
id | The ID of the consignment you wish to retrieve.

<aside class="success">
On success a 200 response code is sent.
</aside>













