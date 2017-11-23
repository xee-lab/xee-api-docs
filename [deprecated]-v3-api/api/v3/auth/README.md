# Auth

This is the authentication route of our API.
It is mandatory to go with them in order to get the user data.

|API|Description|
|---|---|
|[`auth/auth`](auth.md)|For the authentication page|
|[`auth/access_token`](access_token.md)|For the *access token* API|


## Error cases

The *authentication* gives you the `access_token` needed to access any resource with our API.

As you'll notice, this `access_token` should be provided with a specific *header*: the `Authorization` Header.

In almost all our *resource* API, you'll have to specify this *header*

`Authorization: Bearer HAzsa..AZN`

There are 3 kind of errors with the `access_token`:

- It is *missing*
- It is *malformed*
- It is *invalid*


|Reason|Status Code|Type|Message|Tip|
|---|---|---|---|---|
|Missing header|`401`|`AUTHENTICATION_ERROR`|Authorization is missing|Add the Authorization header with a valid access_token|
|Malformed Token|`401`|`AUTHENTICATION_ERROR`|Authorization is malformed|Add the Authorization header with a valid access_token|
|Invalid Token|`401`|`AUTHENTICATION_ERROR`|Invalid token|Try to refresh access_token or ask the user to sign-in again|
|Missing scope|`403`|`AUTHORIZATION_ERROR`|Token does not have the required scope|Add the {neededScope} scope to your app scopes and reconnect the user|
|Expired Token|`403`|`AUTHORIZATION_ERROR`|Token has expired|Refresh the access token and then retry|
|Revoked Token|`403`|`AUTHORIZATION_ERROR`|Token has been revoked|Create a new access token and then retry|