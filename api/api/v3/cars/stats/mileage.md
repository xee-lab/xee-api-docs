# /cars/{carId}/stats/mileage

Get the *mileage* value for a specific *car*

## Basics

`[GET] https://{env}.xee.com/v3/cars/{carId}/stats/mileage?begin={begin}&end={end}&initialValue={initialValue}`

> You'll need the *signals_read* scope.

Secured by **OAuth 2** access token.

> Be aware you can only request one month max interval per request

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
|`carId`|The `id` of the car you are looking for the *mileage*|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`begin`|The start of the interval when you want the *mileage* to be computed, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **First day of month at 00:00:00+00:00**|NO|
|`end`|The end of the interval when you want the *mileage* to be computed, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **Current moment when you send request**|NO|
|`initialValue`|An offset to add to the mileage stat. Default value is **0**|NO|

## Success Response

- Status Code: `200`
- Body:

```javascript 
{
	"beginDate": "2016-07-01T00:00:00Z",
	"endDate": "2016-07-15T12:34:30.447653854Z",
	"type": "MILEAGE",
	"value": 4.2
}
```

|Property|Type|Comment|
|---|---|---|
|beginDate|date|the date when the mileage compute has started|
|endDate|date|the date when the mileage compute has ended|
|type|string|the type of stat, here `MILEAGE`|
|value|double|the *mileage* in *km* between the dates (plus optional initial value)|

## Errors

> See how errors are formed in [v3 Readme](../../README.md)

> Be aware of [authentication errors](../../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|You did not required `signals_read`|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the signals_read scope to your app scopes and reconnect the user|
|The token does not have access to this car|`403`|`AUTHORIZATION_ERROR`|Token can't access this car|Make sure the token belongs to the user owning the car you're asking for|
|The car does not exist|`404`|`PARAMETERS_ERROR`|Car not found|Please check that the car exists, looks like it does not|
|The statistic does not exist|`404`|`PARAMETERS_ERROR`|Statistics not found|Please check that the car exists and data are present, looks like it does not|
|Order of dates is wrong|`416`|`PARAMETERS_ERROR`|Range issue in dates|Please check the dates you've set in parameters are correct and begin is before end|
|You asked for more than the month|`416`|`PARAMETERS_ERROR`|Range issue in dates|You can only request 1 month max per request|