# /auth/access_token

The `access token` route is used to deal with access tokens. You can:

- Obtain one
- Refresh one

## Basics

`[POST] https://cloud.xee.com/v3/auth/access_token`

Secured by **Basic** Authorization.

## Obtain a fresh token

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic: base64(clientId:clientSecret)` with your client information|YES|
|Content-Type|`application/x-www-form-urlencoded`|YES|

### Parameters

For this request, you'll need *2 POST* parameters.

|Parameter name|Parameter value|
|---|---|
|`grant_type`|`authorization_code `|
|`code`|The code you've obtained with the [redirect uri](auth.md)|


And then `POST` it

### Success Response

- Status Code: `200`
- Body:

```javascript
{
    "access_token": "22fe0c13e995da4a44a63a7ff549badb5d337a42bf80f17424482e35d4cca91a",
    "expires_at": 1382962374,
    "expires_in": 3600,
    "refresh_token": "8eb667707535655f2d9e14fc6491a59f6e06f2e73170761259907d8de186b6a1",
    "token_type": "bearer"
}
```

|Property|Type|Comment|
|---|---|---|
|access_token|string|This is the token you will use to consume our APIs|
|expires_at|date|At this date, the `access_token` won't be useful anymore, you'll need to *refresh it* (see bellow)|
|expires_in|long|This is the life duration of the `access_token` in seconds|
|refresh_token|string|This is very important, it will be used to generate a new `access_token` later|
|token_type|string|The type of the token|


### Errors

> See how errors are formed in [v3 Readme](../README.md)

- Reason: If you forgot the `grant_type` or the `code` in the body of the *request*
- Status Code: `400`
- Content

```javascript
[
	{
		"type": "PARAMETERS_ERROR",
		"message": "Missing parameter",
		"tip": "Check you've set the grant_type and the code"
	}
]
```
---
- Reason: The `code` you sent in the *request* is not valid
- Status Code: `403`
- Content

```javascript
{
  "message": "Invalid authentication"
}
```

## Refreshing a token

When an `access_token` is not valid anymore, you can *refresh it*.
The system is very similar to the one used to get a token for the first time.

> The URL is the same

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic: base64(clientId:clientSecret)` with the client information|YES|
|Content-Type|`application/x-www-form-urlencoded`|YES|

### Parameters

For this request, you'll need *2 POST* parameters.

|Parameter name|Parameter value|
|---|---|
|`grant-type`|`refresh_token`|
|`refresh_token`|The *refresh_token* you saved from the first time you asked one|

And then `POST` it

### Success Response

- Status Code: `200`
- Body:

```javascript
{
    "access_token": "22fe0c13e995da4a44a63a7ff549badb5d337a42bf80f17424482e35d4cca91a",
    "expires_at": 1382962374,
    "expires_in": 3600,
    "refresh_token": "8eb667707535655f2d9e14fc6491a59f6e06f2e73170761259907d8de186b6a1",
    "token_type": "bearer"
}
```

|Property|Type|Comment|
|---|---|---|
|access_token|string|This is the token you will use to consume our APIs|
|expires_at|date|At this date, the `access_token` won't be useful anymore, you'll need to *refresh it* (see bellow)|
|expires_in|long|This is the life duration of the `access_token` in seconds|
|refresh_token|string|This is very important, it will be used to generate a new `access_token` later|
|token_type|string|The type of the token|


### Errors

- Reason: If you forgot the `grant_type` or the `code` in the body of the *request*
- Status Code: `400`
- Content

```javascript
[
	{
		"type": "PARAMETERS_ERROR",
		"message": "Missing parameter",
		"tip": "Check you've set the grant_type and the refresh_token"
	}
]
```
---
- Reason: The `refresh_token` you sent in the *request* is not valid
- Status Code: `403`
- Content

```javascript
{
  "message": "Invalid authentication"
}
```
```