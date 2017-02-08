# POST /devices/{xeeId}/associate?pin={pin}

Associate a user and a device specified by its `xeeId`

## Basics

`[POST] https://{env}.xee.com/v3/devices/{xeeId}/associate?pin={pin}`

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
|`pin`|The pin code of the device to associate with the current user|YES|


### Body

No body expected.

## Success Response

- Status Code: `204`

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Wrong device id format, or wrong pin format, or wrong pin code|`400`|`PARAMETER_ERROR`||Check the device id and the pin|
|Scope `devices_management` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the devices_management scope to your app scopes and reconnect the user|
|The token does not have access to this user|`403`|`AUTHORIZATION_ERROR`|Token can't access this user|Make sure the user is accessible with this token|
|Too many association attempts|`403`|`AUTHORIZATION_ERROR`|The box association already failed 3 times||
|Device or user does not exist|`404`|`NOT_FOUND`|Device or user not found|Please check that the device exists, looks like it does not|
|Device already associated|`409`|`CONFLICT`|Device already associated to another user||
