# /brands

Get the list of all brands

## Basics

`[GET] https://cloud.xee.com/v3/compat/brands`

Secured by **Basic** auth.

## Request

### Headers

|Header name|Header value|Mandatory|
|---|---|---|
|Authorization|`Basic` with the `base64` of your `clientId` and  `clientSecret `|YES|

## Success Response

- Status Code: `200`
- Body:

```javascript
[
    {
        "id": 467,
        "name": "ABARTH",
        "displayName": "ABARTH"
    },
    {
        "id": 1,
        "name": "AC",
        "displayName": "AC"
    },
    ...
]
```

The response is an array of brands.

### brand model object

|Property|Type|Comment|
|---|---|---|
|id|int|The identifier of the brand|
|name|string|The default name of the brand|
|displayName|string|The comprehensive name of the brand. For example displayName is `VOLKSWAGEN` for brand with name `VW`|
