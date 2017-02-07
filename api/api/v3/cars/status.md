# /cars/{carId}/status

Get the current *status* of a specific car

## Basics

`[GET] https://{env}.xee.com/v3/cars/{carId}/status`

> You'll need the *status_read* scope.

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
|`carId`|The `id` of the car you are looking for the *status*|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript 
{
    "accelerometer": {
        "x": -768,
        "y": 240,
        "z": 4032,
        "date": "2016-03-01T02:24:20.000000+00:00"
        },
    "location": {
        "latitude": 50.67815,
        "longitude": 3.208155,
        "altitude": 31.8,
        "satellites": 4,
        "heading": 167,
        "date": "2016-03-01T02:24:20.000000+00:00"
    },
    "signals": [
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
}
```

|Property|Type|Comment|
|---|---|---|
|location|location|More on [Locations API page](locations.md)|
|accelerometer|accelerometer||
|signals|signal|More on [Signals API page](signals.md)|

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Scope `status_read` is missing|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the status_read scope to your app scopes and reconnect the user|
|The token does not have access to this car|`403`|`AUTHORIZATION_ERROR`|Token can't access this car|Make sure the token belongs to the user owning the car you're asking for|
|The car does not exist|`404`|`PARAMETERS_ERROR`|Car not found|Please check that the car exists, looks like it does not|

