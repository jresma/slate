---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://api.indinero.com/developer/sign_up'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - api
  - errors

search: true
---

# Introduction

Welcome to the inDinero API! You can use our API to access inDinero API endpoints which can get information on various companies, transactions, reimbursements, and receipts in our database.

inDinero uses API keys to allow access to the API. You can register a new inDinero API key at our [Developer Portal](https://api.indinero.com/).

# Developer Account

To create an account, go to our [Sign Up Page](https://api.indinero.com/developer/sign_up). Once registered, you will be provided with a set of keys for API authentication.

After creating an account, you can now create an application.

## How to create an application

Navigate to the **Applications** tab area of the Developer Portal. Click on `New Application` button. Fill out all the required fields. Use the generated Application Details when doing the authentication.

# Authentication

inDinero API is using OAuth 2.0, the standard used by most APIs for authenticating and authorizing users. We highly suggest you use an OAuth library/wrapper to simplify the process of authenticating.

Your API keys carry many privileges, so be sure to keep them secret! Do not share your secret API keys in publicly-accessible areas such GitHub, client-side code, and so forth.

Navigate to the **Applications** tab area of the [Developer Portal](https://api.indinero.com/) to set your Redirect URL. The Redirect URL is the URL within your application that will receive the OAuth2 credentials.

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
Once the client has obtained an API access token from the previous step, it can be used to make authenticated requests to the API. Authenticated requests are signed with a header pair of `Authorization: Bearer {access_token}` where *{access_token}* is replaced with the permanent token for the user.

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

> To make authenticated requests, use this code:

```shell
curl "indinero_api_endpoint" \
  -H "Authorization: Bearer indinero-user-access-token"
```

> Make sure to replace <code>indinero-user-access-token</code> with your access token.

* Select an endpoint
* Click to OAuth 2.0 tab to indicate you are making a OAuth POST
* In your existing tokens, make sure to add token to header
* Send the `GET` or `POST` request

Unless specified, the API expects the token to be included in the requests to the
server in a header that looks like the following:

`Authorization: Bearer indinero-user-access-token`

<aside class="notice">
  You must replace <code>indinero-user-access-token</code> with the access token the server returns after authorization.
</aside>

# Two-Factor Authentication

The Two-Factor Authentication API requires requests to be authenticated, i.e.
when doing requests to 2FA endpoints requires OAuth2 access token to be specified
in the request headers.

## Opt In

> To opt-in a user, use the following code:

```shell
curl "http://api.indinero.com/api/v2/2fa" \
  -X POST \
  -H "Authorization: Bearer indinero-user-access-token" \
  -d user[cellphone]="317-338-9302" \
  -d user[country_code]="54"
```

> When the call succeeds, the API will return a 200, with the following data:

```json
{ "id": 209 }
```

> When the call failed, the API will return a Bad Request response.

This endpoint opts the user in for Two-Factor Authentication.

### HTTPS Request

`POST https://api.indinero.com/api/v2/2fa`

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
user[cellphone] | | Mobile number to opt in
user[country_code] | | Country code of the mobile number to opt in

## Request Token via SMS

```shell
curl "http://api.indinero.com/api/v2/2fa/sms" \
  -X GET \
  -H "Authorization: Bearer indinero-user-access-token"
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": "SMS token was sent.",
  "cellphone": "+54-XXX-XXX-XX02"
}
```

This endpoint requests Two-Factor token for user via SMS.

### HTTPS Request

`GET https://api.indinero.com/api/v2/2fa/sms`

## Verify Two-Factor Token

> To verify the two-factor token, use the following command:

```shell
curl "https://api.indinero.com/api/v2/2fa/verify" \
  -X POST \
  -H "Authorization: Bearer indinero-user-access-token" \
  -d user[token]="0000000" \
  -d user[remember]="false"
```

> The above command returns JSON structured like this:

```json
{
  "success": "true",
  "message": "Token is valid.",
  "token": "is valid"
}
```

This endpoint verifies Two-Factor token for user.

### HTTPS Request

`POST https://api.indinero.com/api/v2/2fa/verify`

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
user[token] | | Token the user receives from Authy via SMS
user[remember] | false | Set to true to remember the token for the next thirty days.

## Opt Out

> To opt out a user from two-factor authentication, make this call:

```shell
curl "https://api.indinero.com/api/v2/2fa" \
  -X DELETE \
  -H "Authorization: Bearer indinero-user-access-token"
```

> The above command returns JSON structured like this:

```json
{
  "message": "User was removed.",
  "success": true
}
```

This endpoint opts the user out and removes Two-Factor details.

### HTTPS Request

`DELETE https://api.indinero.com/api/v2/2fa`

# Resources
