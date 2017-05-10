# /ktype/{ktype} (*DEPRECATED*)

Get a compatibility from a *ktype*

## Basics

`[GET] https://compat.xee.com/v1/ktype/{ktype}?in_service={in_service}`

Secured by **Basic** auth.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`ktype `|The `ktype` you want the compatibility|YES|

### Query Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`in_service`|The `date` of the first time the car was used. Format is `yyyy-mm` (`2016-04`)|NO|

## Success Response

- Status Code: `200`
- Body:

```javascript
{
    "signalsAvailable": [
    	{
            "name": "Odometer",
            "reliability": null, // DEPRECATED will be removed in a futur version
            "confidence": true,
            "evolution": null
        },
        {
            "name": "FuelLevel",
            "reliability": "incremental", // DEPRECATED will be removed in a futur version
            "confidence": false,
            "evolution": "incremental"
    	}
    ],
    "signalsUnavailable": [
    	{
            "name": "VehiculeSpeed",
            "reliability": null, // DEPRECATED will be removed in a futur version
            "confidence": null,
            "evolution": null
        },
        {
            "name": "EngineSpeed",
            "reliability": null, // DEPRECATED will be removed in a futur version
            "confidence": null,
            "evolution": null
    	}
    ]
}
```

|Property|Type|Comment|
|---|---|---|
|signalsAvailable|array|contains *signals*|
|signalsUnavailable|array|contains *signals*|

#### Signal

|Property|Type|Comment|
|---|---|---|
|name|string||
|reliability|enum (as string)|**DEPRECATED** This field is just use for the FuelLevel signal. Might be null, possible values : `continuous`, `incremental`, `wtf` (**W**ill **T**emporatily **F**ail)|
|confidence|boolean|This field represents the confidence we have on the reliability for this signal. If `true`, the signal is considered as reliable. If `false`, you should not use this signal, unless you checked the `evolution` field before and know what you are doing|
|evolution|enum (as string)|This field is a represents the evolution of the signal. Might be null, possible values : `continuous`, `incremental`, `wtf` (**W**ill **T**emporatily **F**ail). This field is mainly used when the field `confidence` is set to false.|

## Errors

> See how errors are formed in [API v3 Readme](https://github.com/xee-lab/xee-api-docs/tree/master/api/api/v3#errors)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|`ktype` not correct|`400`|`PARAMETERS_ERROR`|Unable to parse KType parameter|Please check if KType parameter you have set is a int|
|`in_service` date not correct|`400`|`PARAMETERS_ERROR`|Unable to parse date|Please check the dates you have set in parameters are correct format `yyyy-mm` (`2016-04`)|
|`ktype` does not exists in Xee|`404`|`NOT_FOUND`|KType not found|Please try with an other KType or specify/change the in_service date.|
