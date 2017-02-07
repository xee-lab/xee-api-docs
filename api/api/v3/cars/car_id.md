# /cars/{carId}

Get a specific *car* from its `id`

## Basics

`[GET] https://{env}.xee.com/v3/cars/{carId}`

> You'll need the *cars_read* scope.

Secured by **OAuth 2** access token.

## Request

### Environment

The `env` variable as the host of the route can be changed for testing purpose.

|Value|Comment|
|---|---|
|`cloud`|**production** environment (*real* client data, `Authorization` needed)|
|`sandbox`|**sandbox** environment (*fake* data, **no** `Authorization` needed)|

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Bearer` with the *OAuth2* access token|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`carId`|The `id` of the car you are looking for|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript 
{
    "id": 1337,
    "name": "Mark-42",
    "make": "Mark",
    "model": "42",
    "year": 2014,
    "numberPlate": "M-42-TS",
    "deviceId": "E133742015",
    "cardbId": 210,
    "creationDate": "2014-09-23T12:49:48+00:00",
    "lastUpdateDate": "2016-02-19T08:41:58+00:00"
}
```

|Property|Type|Comment|
|---|---|---|
|id|integer||
|name|string||
|make|string|Might be `generic`|
|model|string|Might be `null`|
|year|integer|Might be `0`|
|numberPlate|string|Might be `null`|
|deviceId|string|The `serial number` of the device. Might be `null` if the car has no device associated|
|cardbId|integer|Represents the type of the *car* from our point of view, that's how we speak to them|
|creationDate|date||
|lastUpdateDate|date||

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|You did not required `cars_read`|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the cars_read scope to your app scopes and reconnect the user|
|The token does not have access to this car|`403`|`AUTHORIZATION_ERROR`|Token can't access this car|Make sure the token belongs to the user owning the car you're asking for|
|The car does not exist|`404`|`PARAMETERS_ERROR`|Car not found|Please check that the car exists, looks like it does not|