# /cars/{carId}/signals

Get all signals (data) history from a specific *car*

## Basics

`[GET] https://cloud.xee.com/v3/cars/{carId}/signals?limit={limit}&begin={begin}&end={end}&name={name1},{etc...}`

> You'll need the *signals_read* scope.

Secured by **OAuth 2** access token.

> Be aware you can only request one month max interval per request

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Bearer` with the *OAuth2* access token|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`carId`|The `id` of the car you are looking for the *signals*|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`limit`|The maximum number of signals you want in return|NO|
|`begin`|The start of the interval when you want the *signals*, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **First day of month at 00:00:00+00:00**|NO|
|`end`|The end of the interval when you want the *signals*, Format is `2016-04-20T13:37:42Z(+/-HH:mm)` default value is **Current moment when you send request**|NO|
|`name`|The list of *signals* you want, for example, if you want `LockSts` and `Odometer`, you'll have `name=LockSts,Odometer`, by default, all the signals available are sent back. You can see the [full list here](signals_list.md)|NO|

## Success Response

- Status Code: `200`
- Body:

```javascript 
[
  {
	    "name": "LockSts",
	    "value": 0,
	    "date": "2016-03-01T02:24:24.000000+00:00"
  },
  {
	    "name": "Odometer",
	    "value": 34512.1,
	    "date": "2016-03-01T02:24:27.116000+00:00"
  },
  {
  		...
  }
]
```

|Property|Type|Comment|
|---|---|---|
|name|string|The name of the signal|
|value|float|The value of the signal|
|date|date|the date when the signal has been updated|


## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|The limit parameter is wrong|`400`|`PARAMETERS_ERROR`|Limit can't be less than 0|The limit in parameter must ben a positive integer|
|Any signal in parameter is a valid signal name|`400`|`PARAMETERS_ERROR`|Wrong signal name|Can't find any signals with those names|
|You did not required `signals_read`|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the signals_read scope to your app scopes and reconnect the user|
|The token does not have access to this car|`403`|`AUTHORIZATION_ERROR`|Token can't access this car|Make sure the token belongs to the user owning the car you're asking for|
|The car does not exist|`404`|`PARAMETERS_ERROR`|Car not found|Please check that the car exists, looks like it does not|
|Order of dates is wrong|`416`|`PARAMETERS_ERROR`|Range issue in dates|Please check the dates you've set in parameters are correct and begin is before end|
|You asked for more than the month|`416`|`PARAMETERS_ERROR`|Range issue in dates|You can only request 1 month max per request|