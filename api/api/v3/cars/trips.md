# /cars/{carId}/trips

Get the trips history from a specific *car*

## Basics

`[GET] https://{env}.xee.com/v3/cars/{carId}/trips?begin={begin}&end={end}`

> You'll need the *trips_read* scope.

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
|`carId`|The `id` of the car you are looking for the * trips*|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`begin`|The start of the interval when you want the *trips*, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **First day of month at 00:00:00+00:00**|NO|
|`end`|The end of the interval when you want the *trips*, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **Current moment when you send request**|NO|
|`inclusive`|If set to `true`, all the trips started __or__ ended between `begin` and `end` will be returned. If set to `false` (*default value*), only the trips started __and__ ended between `begin` and `end` will be returned.|NO


## Success Response

- Status Code: `200`
- Body:

```javascript 
[
	{
		"id": "56b43a4f051f29071f14218d",
		"beginLocation": {
			"latitude": 50.6817,
			"longitude": 3.08202,
			"altitude": 2,
			"heading": 167.86,
			"satellites": 1,
			"date": "2016-01-29T18:36:17Z"
		},
		"endLocation": {
			"latitude": 50.6817,
			"longitude": 3.08202,
			"altitude": 2,
			"heading": 42.00,
			"satellites": 1,
			"date": "2016-01-29T18:36:17Z"
		},
		"beginDate": "2016-01-29T18:39:17Z",
		"endDate": "2016-01-29T19:15:15Z"
	},
	{
		...
	}
]
```

|Property|Type|Comment|
|---|---|---|
|id|string|An id for the trip|
|beginLocation|location|The first *location* of the trip|
|endLocation|location|The last *location* of the trip|
|beginDate|date|the date when the trip has started|
|endDate|date|the date when the trip has stoped|

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Scope `trips_read` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the trips_read scope to your app scopes and reconnect the user|
|The token does not have access to this car|`403`|`AUTHORIZATION_ERROR`|Token can't access this car|Make sure the token belongs to the user owning the car you're asking for|
|The car does not exist|`404`|`PARAMETERS_ERROR`|Car not found|Please check that the car exists, looks like it does not|
|Order of dates is wrong|`416`|`PARAMETERS_ERROR`|Range issue in dates|Please check the dates you've set in parameters are correct and begin is before end|
|You asked for more than the month|`416`|`PARAMETERS_ERROR`|Range issue in dates|You can only request 1 month max per request|