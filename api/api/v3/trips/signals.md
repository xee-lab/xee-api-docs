# /trips/{tripId}/signals

Get all signals history from a specific *trip*

## Basics

`[GET] https://cloud.xee.com/v3/trips/{tripId}/signals?name={name1},{etc...}`

> You'll need the *trips_read*, *signals_read* scope.

Secured by **OAuth 2** access token.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Bearer` with the *OAuth2* access token|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`tripId`|The `id` of the *trip* you are looking for the * signals*|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`name`|The list of *signals* you want, for example, if you want `LockSts` and `Odometer`, you'll have `&name=LockSts&name,Odometer`, by default, all the signals available are sent back. You can see the [full list here](../cars/signals_list.md)|NO|

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
    ...
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

> It uses [signals API](../cars/signals.md) with pre filled parameters

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|The token does not have access to this trip|`403`|`AUTHORIZATION_ERROR`|Token can't access this trip|Make sure the trip belongs to the user you've got the token from|
|Trip does not exist|`404`|`PARAMETERS_ERROR`|Trip not found|Please check that the trip exists, looks like it does not|