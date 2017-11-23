# /trip/{tripId}/stats/usedtime

Get the *used time* value for a specific *trip*

## Basics

`[GET] https://{env}.xee.com/v3/trips/{tripId}/stats/usedtime`

> You'll need the *trips_read* scope.

Secured by **OAuth 2** access token

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
|`tripId`|The `id` of the trip you are looking for the *used time* (duration)|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript
{
       	"type": "USED_TIME",
       	"value": 1271
}
```

|Property|Type|Comment|
|---|---|---|
|type|string|the type of stat, here `USED_TIME`|
|value|double|the *used time* in *sec*|

## Errors

> See how errors are formed in [v3 Readme](../../../README.md)

> Be aware of [authentication errors](../../../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Scope `trips_read` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the trips_read scope to your app scopes and reconnect the user|
|The token does not have access to this trip|`403`|`AUTHORIZATION_ERROR`|Token can't access this trip|Make sure the token belongs to the user owning the trip you're asking for|
|The trip does not exist|`404`|`PARAMETERS_ERROR`|trip not found|Please check that the trip exists, looks like it does not|
|The statistic does not exist|`404`|`PARAMETERS_ERROR`|Statistics not found|Please check that the trip exists and data are present, looks like it does not|
|Order of dates is wrong|`416`|`PARAMETERS_ERROR`|Range issue in dates|Please check the dates you've set in parameters are correct and begin is before end|
|You asked for more than the month|`416`|`PARAMETERS_ERROR`|Range issue in dates|You can only request 1 month max per request|