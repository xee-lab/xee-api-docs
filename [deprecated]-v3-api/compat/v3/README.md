# v3

New Xee Compatibility API

## Authentication

The authentication is based on `Basic`.
When you register on [dev space](https://dev.xee.com) and create an application, you get a `clientId` and a `clientSecret`.

Then, for each request, provide an `Authorization` header with the following value:
`Basic base64(clientId:clientSecret)`

For example: *Basic ZlV5YlhtVG......RDdjeU1................LaUdwUU9MRlFpUko=*

## API

|API|Description|
|---|---|
|[`/brands`](brands.md)|Get brands list|
|[`/brands/{brandId}/models`](models.md)|Get models for a *brand Id*|
|[`/brands/{brandId}/models/versions?model=modelString`](versions.md)|Get versions for a *brand Id* and a *model* string|
|[`/ktypes?plateNumber=aa123aa&captchaResponse=xxx`](versionsByPlateNumber.md)|Get versions from a *plateNumber*. This API is protected by a Captcha.|
|[`/ktype/{ktype}`](ktype.md)|*DEPRECATED* Get compatibility from a *ktype*|
|[`/ktypes/{ktype}`](ktype.md)|Get compatibility from a *ktype*|
|[`/cardb/{cardbId}`](cardb.md)|Get compatibility from a *cardb Id*|

## Errors

Specific authentication errors here

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Missing `Authorization` header|`401`|`AUTHENTICATION_ERROR`|Authorization header is not valid|Make sure that the header has a valid format|

