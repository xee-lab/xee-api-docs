# POST /devices/{xeeId}/dissociate

Dissociate the device specified by its `deviceId` and the car

## Basics

`[POST] https://{env}.xee.com/v3/devices/{deviceId}/dissociate`

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
|`deviceId`|The `id` of the device you want to dissociate|YES|

### Body

No body expected.

## Success Response

- Status Code: `204`

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Wrong device id format|`400`|`PARAMETER_ERROR`||Check the device id|
|Scope `devices_management` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the devices_management scope to your app scopes and reconnect the user|
|The token does not have access to this user|`403`|`AUTHORIZATION_ERROR`|Token can't access this user|Make sure the user is accessible with this token|
|Device or car does not exist|`404`|`NOT_FOUND`|Device or car not found|Please check that the device exists, looks like it does not|
|Device not associated|`409`|`CONFLICT`|The box is not already associated to a user||
