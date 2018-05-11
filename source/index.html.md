---
title: eTrak API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php

toc_footers:
  - <a href="https://etrak.io">Sign Up for a Developer Key</a>
  
includes:
  - errors

search: true
---



# Introduction

Welcome to the eTrak API Reference.

## PHP SDK

There's a PHP SDK available for this API. You can download it here.



# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.etrak.io/helloworld"
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

```shell
# tbc
```

```php
<?
// tbc
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









## CreateApiKey

```shell
# tbc
```

```php
<?
// tbc
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










# Users

Users are people who can log in and manage your eTrak.io account.

<aside class="notice">
  You can manage users from your eTrak.io account online too.
</aside>

## List All Users

```shell
# tbc
```

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









## Get A User

```shell
# tbc
```

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








## Create A User

```shell
# tbc
```

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










## Update A User

```shell
# tbc
```

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







## Delete A User

```shell
# tbc
```

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

```shell
# tbc
```

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








## Update Your Account

```shell
# tbc
```

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


























# Contracts

Contracts represent the commercial agreements you have with eTrak.

## List All Contracts

```shell
# tbc
```

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









## Get A Contract

```shell
# tbc
```

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











<!--


# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

-->