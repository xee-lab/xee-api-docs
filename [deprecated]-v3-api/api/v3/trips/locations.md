# /trips/{tripId}/locations

Get the locations history from a specific *trip*

## Basics

`[GET] https://{env}.xee.com/v3/trips/{tripId}/locations`

> You'll need the, *trips_read* and *locations_read* scope.

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
|`tripId`|The `id` of the *trip* you are looking for the *locations*|YES|

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
|satCount|integer|Number of satellites used to determine location|
|heading|integer|Direction|
|date|date|the date when the location has been found|


## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

> It uses [location API](../cars/locations.md) with pre filled parameters

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|The token does not have access to this trip|`403`|`AUTHORIZATION_ERROR`|Token can't access this trip|Make sure the trip belongs to the user you've got the token from|
|Trip does not exist|`404`|`PARAMETERS_ERROR`|Trip not found|Please check that the trip exists, looks like it does not|