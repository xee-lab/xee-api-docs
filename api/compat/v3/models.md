# /brands/{brandId}/models

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

## Success Response

- Status Code: `200`
- Body:

```javascript
[
    {
        "brandId": 467,
        "model": "124 Spider (348_)",
        "minStartDate": "2016-03-01T00:00:00Z",
        "maxEndDate": null,
        "cardbid": 426,
        "connection": [{
                "type": "wired",
                "link": null
            },
            {
                "type": "plugandgo",
                "link": null
            }
        ],
        "category": "124"
    },
    {
        "brandId": 467,
        "model": "500 / 595 (312_)",
        "minStartDate": "2008-08-01T00:00:00Z",
        "maxEndDate": null,
        "cardbid": null,
        "connection": null,
        "category": "500"
    },
     ...
    {
        "brandId": 467,
        "model": "GRANDE PUNTO (199_)",
        "minStartDate": "2007-12-01T00:00:00Z",
        "maxEndDate": "2012-12-01T00:00:00Z",
        "cardbid": 140,
        "connection": [{
            "type": "plugandgo",
            "link": null
        }],
        "category": "GRANDE"
    },
    ...
]
```

The response is an array of models.

### model object

|Property|Type|Comment|
|---|---|---|
|brandId|int|The identifier of the brand|
|model|string|The model string of the model|
|minStartDate|date|The minimum start date within all the versions for this model|
|maxEndDate|date|The maximum end date within all the versions for this model|
|cardbid|int|The cardb id for this model. **/!\\** This field will be populated *only* if *all the versions* of this model have the same cardb id. So if this field is `null` you will have to look for your exact version to get the cardb id.|
|connection|array(connection)|The available mounting connections for XeeCONNECT for this model. **/!\\** This field will be populated *only* if *all the versions* of this model have common mounting connection informations. So if this field is `null` you will have to look for your exact version to get the cardb id.|
|category|string|The model category, if you want to group all the models with the same category. For example all the BMW 1 models will have the same category "Série 1"|

### connection object

|Property|Type|Comment|
|---|---|---|
|type|enum(plugandgo\|wired)|The mounting type for this model. `plugandgo` means "On Board Diagnostics" plug compatible, and `wired` means that hidden mounting is mandatory for this model|
|link|string|The URL to the mounting manual for this model. For now this property will always be `null`|


