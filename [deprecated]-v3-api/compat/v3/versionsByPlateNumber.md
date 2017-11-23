# /ktypes?plateNumber=aa123aa&captchaResponse=xxx

Get versions and ktypes from a *plateNumber*

## Basics

`[GET] https://cloud.xee.com/v3/compat/ktypes?plateNumber=aa123aa&captchaResponse=xxx`

Secured by **Basic** auth.


## Captcha

This API is secured by a reCAPTCHA verification.

You MUST add this captcha to your website if you want to use this API.

The documentation of reCAPTCHA for client-side implementation can be found here: https://developers.google.com/recaptcha/docs/display

Once you got the `recaptcha-response`, you will have to pass it to this API to be able to perform the search.

For us to be able to make the captcha verification, you will need to use OUR reCAPTCHA site key : `6Ld4nSUUAAAAAH1onUr4ql7UBuYqdLLzmonyo_R0`

*IMPORTANT*: Since this captcha usage is restricted to certain domains names, to enable the captcha on your website, please contact `support[@]xee.com` in order to whitelist your domain name.


## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`plateNumber`|The plate number to search|YES|
|`captchaResponse`|The recaptcha response|YES|

## Success Response

This API can return multiple versions, since sometimes a given plate number is associated to multiple ktypes.

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
