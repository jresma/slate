---
title: API Reference

language_tabs:
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the inDinero API! You can use our API to access inDinero API endpoints, which can get information on various companies, transactions, reimbursements, and receipts in our database.

inDinero uses API keys to allow access to the API. You can register a new inDinero API key at our [developer portal](https://api.indinero.com/).

# Developer Account

To create an account, go to our [sign up page](https://api.indinero.com/developer/sign_up). Once registered, you will be provided with a set of keys for API authentication.

After creating an account, you can now create an application.

## How to create an application

Navigate to the **Applications** tab area of the Developer Portal. Click on `New Application` button. Fill out all the required fields. Use the generated Application Details when doing the authentication.

# Authentication

inDinero API is using OAuth 2.0, the standard used by most APIs for authenticating and authorizing users. We highly suggest you use an OAuth library/wrapper to simplify the process of authenticating.

Your API keys carry many privileges, so be sure to keep them secret! Do not share your secret API keys in publicly-accessible areas such GitHub, client-side code, and so forth.

Navigate to the **Applications** tab area of the [developer portal](https://api.indinero.com/) to set your Redirect URL. The Redirect URL is the URL within your application that will receive the OAuth2 credentials.

**Base URL:** `https://api.indinero.com`

**Authorization URL:** `https://api.indinero.com/authorize`

**Access Token URL:** `https://api.indinero.com/oauth/token`

## Steps

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

### 1. Ask User for API Access Permission
The first step of process is to prompt the user for authorization. To display the prompt, redirect the user to authenticate through the Authorization URL in a **POST:** `https://api.indinero.com/authorize?response_type=code&scope=&client_id={api_key}&redirect_uri={redirect_uri}&state={state}`.

### 2: Request an OAuth Token
After successfully authenticating in the prompt, inDinero will respond with an authorization code to be used in the Access Token URL: `https://api.indinero.com/oauth/token?client_id={api_key}&client_secret={client_secret}&code={authorization_code}&grant_type=authorization_code&redirect_uri={redirect_uri}`

### 3: Making authenticated requests
Once the client has obtained an API access token from the previous step, it can used to make authenticated requests to the API. Authenticated requests are signed with a header pair of `Authorization: Bearer {access_token}` where *{access_token}* is replaced with the permanent token for the user.

## Postman

Postman is a powerful API testing and development suite used to help developers explore our Public API.

### Download Postman
Download and Install the [Postman Packaged Chrome Application](https://www.getpostman.com/)

### Retrieve a Token

* Navigate to the API Credentials area of the Developer Portal to set your Redirect URL to `https://www.getpostman.com/oauth2/callback`
* Select the OAuth 2.0 Tab in Postman and paste in your:
    * Authorization URL
    * Access Token URL
    * Client ID
    * Client Secret
* Click Get Access Token
* Authenticate / Approve Access with inDinero in the popup window
* Name and Save the retrieved token

### Making Authenticated Requests
* Select an endpoint
* Click to OAuth 2.0 tab to indicate you are making a OAuth POST
* In your existing tokens, make sure to add token to header
* Send the `GET` or `POST` request

# Categories

A chart of accounts is a listing of the names of the accounts that a company has identified and made available for recording trransactions in its general ledger. A company has the flexibility to tailor its chart of accounts to best suit its needs, including adding accounts as needed.

## Get All Categories

``` ruby
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 654321,
    "name": "Category 1",
    "mastercategory": 654321,
    "built_in": true,
    "transaction_type_name": "both"
  },
  {
    "id": 765432,
    "name": "Category 2",
    "mastercategory": 765432,
    "built_in": false,
    "transaction_type_name": "spending"
  },
]
```

This endpoint retrieves all categories.

### HTTPS Request

`GET https://api.indinero.com/api/v2/categories`


# Transactions

An accounting transaction is a business event having a monetary impact on the financial statements of a business. It is recorded in the accounting records of the business.

## Get All Transactions

``` ruby
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 310741769,
    "company_id": 12345,
    "amount": "100.2",
    "real_amount": "-100.2",
    "account_id": 11905941,
    "post_date": "2016-04-18T00:00:00.000Z",
    "container_type": "bank",
    "description_user": null,
    "description_auto": "Home Depot",
    "detail": "Home Depot",
    "memo": "bathroom, kitchen",
    "base_type": "debit",
    "currency_code": null,
    "split_id": -1,
    "category_id": 123456
  },
  {
    "id": 310741768,
    "company_id": 12345,
    "amount": "10000.0",
    "real_amount": "10000.0",
    "account_id": 11905941,
    "post_date": "2016-04-18T00:00:00.000Z",
    "container_type": "bank",
    "description_user": null,
    "description_auto": "Paypal",
    "detail": "Paypal",
    "memo": "deposit",
    "base_type": "credit",
    "currency_code": null,
    "split_id": -1,
    "category_id": 234567
  }
]
```

This endpoint retrieves all transactions.

### HTTPS Request

`GET https://api.indinero.com/api/v2/transactions`

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
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

