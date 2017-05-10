# /cardb/{cardbId} (*DEPRECATED*)

Get a compatibility from a *cardbId*

## Basics

`[GET] https://compat.xee.com/v1/cardb/{cardbId}`

Secured by **Basic** auth.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`cardbId`|The `cardbId` you want the compatibility|YES|

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
|`carDb` not correct|`400`|`PARAMETERS_ERROR`|Unable to parse cardb parameter|Please check if carDb parameter you have set is a int|
|`carDb` not found|`404`|`NOT_FOUND`|CarDb not found|The carDb associated with KType doesn't exist. Please try with an other KType.|
