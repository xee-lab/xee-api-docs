# /ktype/{ktype}

Get a compatibility from a *ktype*

## Basics

`[GET] https://cloud.xee.com/v3/compat/ktypes/{ktype}`

Secured by **Basic** auth.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|

### Url Parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`ktype`|The `ktype` you want the compatibility|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript
{
    "signalsAvailable": [{
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
    "signalsUnavailable": [{
            "name": "VehiculeSpeed",
            "confidence": null,
            "evolution": null
        },
        {
            "name": "EngineSpeed",
            "confidence": null,
            "evolution": null
        }
    ],
    "mounting": {
        "analyzed": true,
        "can": true,
        "connection": [{
                "type": "wired",
                "link": null
            },
            {
                "type": "plugandgo",
                "link": null
            }
        ]
    }
}
```

|Property|Type|Comment|
|---|---|---|
|signalsAvailable|array|Contains all the available *signal* objects for this ktype|
|signalsUnavailable|array|Contains all the unavailable *signal* objects for this ktype|
|mounting|mounting|Contains mounting information|

#### signal object

|Property|Type|Comment|
|---|---|---|
|name|string||
|confidence|boolean|This field represents the confidence we have on the reliability for this signal. If `true`, the signal is considered as reliable. If `false`, you should not use this signal, unless you checked the `evolution` field before and know what you are doing|
|evolution|enum (as string)|This field is a represents the evolution of the signal. Might be null, possible values : `continuous`, `incremental`, `wtf` (**W**ill **T**emporatily **F**ail). This field is mainly used when the field `confidence` is set to false.|


### mounting object

|Property|Type|Comment|
|---|---|---|
|analyzed|boolean|`true` if this ktype has been analyzed|
|can|boolean|`true` if the ktype has can|
|connection|array(connection)|The available mounting connections for XeeCONNECT for this ktype|


### connection object

|Property|Type|Comment|
|---|---|---|
|type|enum(plugandgo\|wired)|The mounting type for this model. `plugandgo` means "On Board Diagnostics" plug compatible, and `wired` means that hidden mounting is mandatory for this model|
|link|string|The URL to the mounting manual for this model. For now this property will always be `null`|


## Errors

> See how errors are formed in [API v3 Readme](https://github.com/xee-lab/xee-api-docs/tree/master/api/api/v3#errors)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|`carDb` not correct|`400`|`PARAMETERS_ERROR`|Unable to parse ktype parameter|Please check if ktype parameter you have set is an int|
|`carDb` not found|`404`|`NOT_FOUND`|`ktype` not found|Please try with an other KType.|
