# /brands/{brandId}/models/version?model=modelString

Get the models list for a *brand Id*

## Basics

`[GET] https://cloud.xee.com/v3/compat/brands/{brandId}/models`

Secured by **Basic** auth.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`brandId`|The brand id field|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`model`|The model you want to get the versions|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript
[
    {
        "ktype": 16982,
        "engineCapacity": "1198",
        "enginePower": 85,
        "fiscalHorsepower": 115,
        "startDate": "2012-03-01T00:00:00Z",
        "endDate": null,
        "brandId": 353,
        "model": "MEGANE III 3/5 portes (BZ0_)",
        "body": "3/5 portes",
        "version": "1.2 TCe",
        "fuel": "Essence",
        "cardbid": 100
    },
    {
        "ktype": 29953,
        "engineCapacity": "1397",
        "enginePower": 96,
        "fiscalHorsepower": 130,
        "startDate": "2009-04-01T00:00:00Z",
        "endDate": null,
        "brandId": 353,
        "model": "MEGANE III 3/5 portes (BZ0_)",
        "body": "3/5 portes",
        "version": "1.4 TCe (BZ0F, BZ1V)",
        "fuel": "Essence",
        "cardbid": 100
    },
    ...
]
```

The response is an array of versions.

### version object

|Property|Type|Comment|
|---|---|---|
|brandId|int|The identifier of the brand|
|model|string|The model string of the model|
|startDate|date|The start date for this version|
|endDate|date|The end date for this version|
|cardbid|int|The cardb id for this version|
|body|string|The body of the version|
|version|string|The version|
|fuel|string|The fuel for this version. For the list of possible values, see below|
|ktype|int|The ktype|
|engineCapacity|string|The engine capacity (unit: cm3)|
|enginePower|int|The engine power (unit: kW)|
|fiscalHorsepower|int|The engine power (unit: CV)|


### fuel field

The fuel field is directly mapped from tecdoc, so it is not possible to ensure you the full list of possible values.

By the way, this is the full list of values extracted on 05/11/2017:

```javascript
[
    "Alcool",
    "Bifuel",
    "Diesel",
    "Diesel/électrique",
    "éléctrique",
    "Essence / gaz combustible liquéfié (GPL)",
    "Essence / éthanol / gaz",
    "Essence / éthanol / électrique",
    "Essence / éthanol",
    "Essence /gaz naturel (CNG)",
    "Essence",
    "Essence/électrique",
    "Flexfuel",
    "Flexfuel/éléctrique",
    "GNC",
    "Hydrogène",
    "LPG",
    "Mélange"
]
```
