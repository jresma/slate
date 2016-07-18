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

To create an account go to our [sign up page](https://api.indinero.com/developer/sign_up). Once registered, you will be provided with a set of keys for API authentication.

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
Once the client has obtained an API access token from the previous step, it can used to make authenticated requests to the API. Authenticated requests are signed with a header pair of `access_token: {access_token}` where *{access_token}* is replaced with the permanent token for the user.

# 2-Factor Authentication

## Register User
```shell
curl "http://api.indinero.com/api/v2/two_factor/new?api_key=d57d919d11e6b" \
-d user[email]="user@domain.com" \
-d user[cellphone]="317-338-9302" \
-d user[country_code]="54"
```

> The above command returns JSON structured like this:

```json
{
  "message": "User created successfully.",
  "user": {
    "id": 209
  },
  "success": true
}
```

This endpoint registers user to two factor.
###HTTPS Request
`POST https://api.indinero.com/api/v2/two_factor/new?api_key={KEY}`

## Request Token
```shell
curl -i "http://api.indinero.com/api/v2/two_factor/sms/209?api_key=d57d919d11e6b"
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": "Token was sent.",
  "cellphone": "+54-XXX-XXX-XX02"
}
```

This endpoint requests two factor token for user.
###HTTPS Request
`GET https://api.indinero.com/api/v2/two_factor/sms/{AUTHY_ID}?api_key={KEY}`

###Force SMS
You can pass in a `force=true` parameter to this api. This will force the SMS to be send even if the user is using the Authy App.

## Verify Token
```shell
curl -i "https://api.indinero.com/api/v2/two_factor/verify/0000000/209?api_key=d57d919d11e6b"
```

> The above command returns JSON structured like this:

```json
{
  "success": "true",
  "message": "Token is valid.",
  "token": "is valid"
}
```

This endpoint verifies two factor token of user.
###HTTPS Request
`GET https://api.indinero.com/api/v2/two_factor/verify/{TOKEN}/{AUTHY_ID}?api_key={KEY}`

###Force Validation
You can pass in a `force=true` parameter to this api to check the user regardless of an unfinished registration.

## Delete User
```shell
curl -i "https://api.indinero.com/api/v2/two_factor/users/209/delete?api_key=d57d919d11e6b"
```

> The above command returns JSON structured like this:

```json
{
  "message": "User was added to remove.",
  "success": true
}
```

This endpoint removes two factor details from user.
###HTTPS Request
`POST https://api.indinero.com/api/v2/two_factor/users/{USER_ID}/delete?api_key={KEY}`

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

