# v1 (DEPRECATED)

The first version of Xee Compatibility API (*DEPRECATED*)

## Authentication

The authentication is based on `Basic`.
When you register on [dev space](https://dev.xee.com) and create an application, you get a `clientId` and a `clientSecret`.

Then, with all the request, provide an `Authorization` header with the following value:
`Basic base64(clientId:clientSecret)`

For example: *Basic ZlV5YlhtVG......RDdjeU1................LaUdwUU9MRlFpUko=*

## API

### Ktype

This is the first route of our API, from this, you can get compatibility from a **Ktype**
> [Ktype API](ktype/README.md)

|API|Description|
|---|---|
|[`/ktype/{ktype}`](ktype/ktype.md)|Get compatibility from a *ktype*|

### Cardb

This is the second route of our API, from this, you can get compatibility from a **cardb**
> [Cardb API](cardb/README.md)

|API|Description|
|---|---|
|[`/cardb/{cardbId}`](cardb/cardbId.md)|Get compatibility from a *cardb Id*|

## Errors

Specific authentication errors here

|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Missing `Authorization` header|`401`|`AUTHENTICATION_ERROR`|Authorization header is not valid|Make sure that the header has a valid format|

