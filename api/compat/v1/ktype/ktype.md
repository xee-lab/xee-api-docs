# /ktype/{ktype}

Get a compatibility from a *ktype*

## Basics

`[GET] https://compat.xee.com/v1/ktype/{ktype}?inservice={inservice}`

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
|`inservice`|The `date` of the first time the car was used. Format is `yyyy-mm` (`2016-04`)|NO|

## Success Response

- Status Code: `200`
- Body:

```javascript
{
    "signalsAvailable": [
    	{
    		"name": "Odometer",
    		"reliability": null
    	},
    	{
    		"name": "FuelLevl",
    		"reliability": "incremental"
    	}
    ],
    "signalsUnavailable": [
    	{
    		"name": "VehiculeSpeed",
    		"reliability": null
    	},
    	{
    		"name": "EngineSpeed",
    		"reliability": null
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
|reliability|enum (as string)|This field is just use for the FuelLevel signal. Might be null, possible values : `continuous`, `incremental`, `wtf` (**W**ill **T**emporatily **F**ail)|

## Errors

> See how errors are formed in [API v3 Readme](https://github.com/xee-lab/xee-api-docs/tree/master/api/api/v3#errors)

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|`ktype` not correct|`400`|`PARAMETERS_ERROR`|Unable to parse KType parameter|Please check if KType parameter you have set is a int|
|`inservice` date not correct|`400`|`PARAMETERS_ERROR`|Unable to parse date|Please check the dates you have set in parameters are correct format `yyyy-mm` (`2016-04`)|
|`ktype` does not exists in Xee|`404`|`NOT_FOUND`|KType not found|Please try with an other KType or specify/change the inService date.|

