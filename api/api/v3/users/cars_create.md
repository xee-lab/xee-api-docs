# POST /users/{userId}/cars

Create a car for a *user* specified by its `id`

## Basics

`[POST] https://{env}.xee.com/v3/users/{userId}/cars`

> You'll need the *cars_write* scope.

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
|`userId`|The `id` of the user you are looking for the *cars*|YES|

### Body

|Parameter name|Type|Description|Mandatory|Rules|
|---|---|---|---|---|
|name|string|The car name|false|length(0,64)|
|make|string|The car manufacturer name|true|length(3,64)|
|model|string|The car model|true|length(1,64)|
|year|integer|The year of production of the car|false|-|
|numberPlate|string|The numberplate of the car|false|length(0,64)|
|timezone|string|The timezone of the country where this car is located|false, default to Europe/Paris|Timezone exists|

## Success Response

- Status Code: `201`
- Body:

```json
{
    "id": 1337,
    "userId": 1234,
    "name": "Mark-42",
    "make": "Mark",
    "model": "42",
    "year": 2014,
    "numberPlate": "M-42-TS",
    "timezone": "Europe/Paris",
    "deviceId": null,
    "cardbId": 210,
    "creationDate": "2014-09-23T12:49:48+00:00",
    "lastUpdateDate": "2016-02-19T08:41:58+00:00"
}
```

|Property|Type|Comment|
|---|---|---|
|id|integer||
|userId|integer||
|name|string||
|make|string|Might be `generic`|
|model|string|Might be `null`|
|year|integer|Might be `0`|
|numberPlate|string|Might be `null`|
|timezone|string|Default value to Europe/Paris|
|deviceId|string|The `serial number` of the device. Might be `null` if the car has no device associated|
|cardbId|integer|Represents the type of the *car* from our point of view, that's how we speak to them|
|creationDate|date||
|lastUpdateDate|date||

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|You did not required `cars_write`|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the cars_write scope to your app scopes and reconnect the user|
|The token does not have access to this user|`403`|`AUTHORIZATION_ERROR`|Token can't access this user|Make sure the user is accessible with this token|
|User does not exist|`404`|`PARAMETERS_ERROR`|User not found|Please check that the user exists, looks like it does not|
