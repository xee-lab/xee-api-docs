# POST /devices/{xeeId}/associate?carId={carId}

Associate a car and a device specified by its `xeeId`

## Basics

`[POST] https://{env}.xee.com/v3/devices/{xeeId}/associate?carId={carId}`

> You'll need the *devices_management* scope.

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
|`xeeId`|The `id` of the device you want to associate|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`carId`|The id of the car you want to associate with the current user|YES|


### Body

No body expected.

## Success Response

- Status Code: `204`

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Wrong device id format, or wrong carId format, or wrong carId|`400`|`PARAMETER_ERROR`||Check the device id, or the car id|
|Scope `devices_management` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the devices_management scope to your app scopes and reconnect the user|
|The token does not have access to this user|`403`|`AUTHORIZATION_ERROR`|Token can't access this user|Make sure the user is accessible with this token|
|Device or car or user does not exist|`404`|`NOT_FOUND`|Device or car or user not found|Please check that the device exists, looks like it does not|
|Device already associated|`409`|`CONFLICT`|The box is not already associated to a user||
