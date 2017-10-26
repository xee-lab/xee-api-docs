# /cardb/{cardbId}

Get a compatibility from a *cardb id*

## Basics

`[GET] https://cloud.xee.com/v3/compat/cardb/{cardbId}`

Secured by **Basic** auth.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|
|Accept-Language|The language in which you want to get the mounting manual link. Available languages are: fr,de,en,es,it,nl,pt|NO : default value is fr|

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
            "name": "GPS",
            "confidence": true,
            "evolution": null
        },
        {
            "name": "Odometer",
            "confidence": true,
            "evolution": null
        },
        {
            "name": "FuelLevel",
            "confidence": false,
            "evolution": "incremental"
    	}
    ],
    "signalsUnavailable": [
    	{
            "name": "VehiculeSpeed",
            "confidence": null,
            "evolution": null
        },
        {
            "name": "EngineSpeed",
            "confidence": null,
            "evolution": null
    	}
    ]
}
```

|Property|Type|Comment|
|---|---|---|
|signalsAvailable|array|Contains all the available *signal* objects for this cardb id|
|signalsUnavailable|array|Contains all the unavailable *signal* objects for this cardb id|

#### Signal

|Property|Type|Comment|
|---|---|---|
|name|string||
|confidence|boolean|This field represents the confidence we have on the reliability for this signal. If `true`, the signal is considered as reliable. If `false`, you should not use this signal, unless you checked the `evolution` field before and know what you are doing|
|evolution|enum (as string)|This field is a represents the evolution of the signal. Might be null, possible values : `continuous`, `incremental`, `wtf` (**W**ill **T**emporatily **F**ail). This field is mainly used when the field `confidence` is set to false.|

## Errors

> See how errors are formed in [API v3 Readme](https://github.com/xee-lab/xee-api-docs/tree/master/api/api/v3#errors)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|`carDb` not correct|`400`|`PARAMETERS_ERROR`|Unable to parse cardb parameter|Please check if carDb parameter you have set is a int|
|`carDb` not found|`404`|`NOT_FOUND`|CarDb not found|The carDb associated with KType doesn't exist. Please try with an other KType.|
