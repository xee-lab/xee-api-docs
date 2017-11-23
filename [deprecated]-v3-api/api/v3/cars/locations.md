# /cars/{carId}/locations

Get the locations history from a specific *car*

## Basics

`[GET] https://{env}.xee.com/v3/cars/{carId}/locations?limit={limit}&begin={begin}&end={end}`

> You'll need the *locations_read* scope.

Secured by **OAuth 2** access token.

> Be aware you can only request one month max per request

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
|`carId`|The `id` of the car you are looking for the *locations*|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`limit`|The maximum number of locations you want in return|NO|
|`begin`|The start of the interval when you want the *locations*, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **First day of month at 00:00:00+00:00**|NO|
|`end`|The end of the interval when you want the *locations*, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **Current moment when you send request**|NO|

## Success Response

- Status Code: `200`
- Body:

```javascript 
[
	{
	    "latitude": 50.67815,
	    "longitude": 3.208155,
	    "altitude": 31.8,
	    "satellites": 4,
	    "heading": 167,
	    "date": "2016-03-01T02:24:20.000000+00:00"
	},
	{
		...
	}
]
```

|Property|Type|Comment|
|---|---|---|
|latitude|float||
|longitude|float||
|altitude|float||
|satellites|integer|Number of satellites used to determine location|
|heading|integer|direction|
|date|date|the date when the location has been found|

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|The limit parameter is wrong|`400`|`PARAMETERS_ERROR`|Limit can't be less than 0|The limit in parameter must ben a positive integer|
|Scope `locations_read` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the locations_read scope to your app scopes and reconnect the user|
|The token does not have access to this car|`403`|`AUTHORIZATION_ERROR`|Token can't access this car|Make sure the token belongs to the user owning the car you're asking for|
|The car does not exist|`404`|`PARAMETERS_ERROR`|Car not found|Please check that the car exists, looks like it does not|
|Order of dates is wrong|`416`|`PARAMETERS_ERROR`|Range issue in dates|Please check the dates you've set in parameters are correct and begin is before end|
|You asked for more than the month|`416`|`PARAMETERS_ERROR`|Range issue in dates|You can only request 1 month max per request|