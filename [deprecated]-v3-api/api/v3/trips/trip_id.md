# /trips/{tripId}

Get a specific trip

## Basics

`[GET] https://{env}.xee.com/v3/trips/{tripId}`

> You'll need the *trips_read* scope.

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
|`tripId`|The `id` of the trip you are looking for|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript
{
    "id": "56b43a4f051f29071f14218d",
    "beginLocation": {
        "latitude": 50.6817,
        "longitude": 3.08202,
        "altitude": 2,
        "heading": 0,
        "satellites": 1,
        "date": "2016-01-29T18:36:17Z"
    },
    "endLocation": {
        "latitude": 50.6817,
        "longitude": 3.08202,
        "altitude": 2,
        "heading": 0,
        "satellites": 1,
        "date": "2016-01-29T18:36:17Z"
    },
    "beginDate": "2016-01-29T18:39:17Z",
    "endDate": "2016-01-29T19:15:15Z",
    "mileage": 21.67,
    "usedTime": 1908
}
```

|Property|Type|Comment|
|---|---|---|
|id|string|The id of the trip|
|beginLocation|location|The first *location* of the trip|
|endLocation|location|The last *location* of the trip|
|beginDate|date|the date when the trip has started|
|endDate|date|the date when the trip has stoped|
|mileage|double|the distance of the trip in kilometers|
|usedTime|integer|the total time of the trip|

## Errors

> See how errors are formed in [v3 Readme](../README.md)

> Be aware of [authentication errors](../auth/README.md)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|The token does not have access to this trip|`403`|`AUTHORIZATION_ERROR`|Token can't access this trip|Make sure the trip belongs to the user you've got the token from|
|Trip does not exist|`404`|`PARAMETERS_ERROR`|Trip not found|Please check that the trip exists, looks like it does not|