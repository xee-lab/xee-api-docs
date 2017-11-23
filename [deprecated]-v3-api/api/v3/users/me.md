# /users/me

Get user from an `access_token`

## Basics

`[GET] https://cloud.xee.com/v3/users/me`

> You'll need the *users_read* scope.

Secured by **OAuth 2** access token.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Bearer` with the *OAuth2* access token|YES|

### Parameters

There is *no parameter* for this API

## Success Response

- Status Code: `200`
- Body:

```javascript 
{
    "id": 42,
    "lastName": "Doe",
    "firstName": "John",
    "nickName": "Johny",
    "gender": "MALE",
    "birthDate": "2016-01-11T00:00:00+00:00",
    "licenceDeliveryDate": "2014-08-13T00:00:00+00:00",
    "role": "dev",
    "isLocationEnabled": true,
    "creationDate": "2014-08-13T15:20:58+00:00",
    "lastUpdateDate": "2016-02-12T09:07:47+00:00",
}
```

|Property|Type|Comment|
|---|---|---|
|id|integer||
|lastName|string||
|firstName|string||
|nickName|string|Might be `null`|
|gender|enum (as string)|`MALE`, `FEMALE`|
|birthDate|date|Might be `null`|
|licenceDeliveryDate|date|Might be `null`|
|role|enum (as string)|`user`, `dev`, others|
|isLocationEnabled|boolean|`true` if the user has authorized us to retrieve the Xee's locations, `false` otherwise|
|creationDate|date||
| lastUpdateDate|date||

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Scope `users_read` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the users_read scope to your app scopes and reconnect the user|