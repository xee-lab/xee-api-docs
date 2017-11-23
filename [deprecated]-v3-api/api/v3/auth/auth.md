# /auth/auth

This API is used to show the user a webview to sign in.

## Basics

`[GET] https://cloud.xee.com/v3/auth/auth?client_id={client_id}&scope={scope}&redirect_uri={redirect_uri}&state={state}`

Secured by **Nothing**

## How it works

### Headers

No headers needed here

### Query parameters

|Parameter name|Parameter value|Mandatory|
|---|---|---|
|`client_id`|The `client id` of your application|YES|
|`scope`|The list of `scopes`, split by a *space* and *url encoded*|NO|
|`redirect_uri`|The `uri` our server will *redirect* to once the user has entered its credentials|NO|
|`state`|An optional state to identify the user from your side|NO|


### Example

`[GET] https://cloud.xee.com/v3/auth/auth?client_id=azerty&scope=users_read+cars_read`

This is the *url* to call when your client:

- Has `azerty` for the client id
- Wants to access `users_read` and `cars_read` scopes
- Has no `redirect URI`
- Has no `state`

Once the user clicks *Connect*, we will check the user/password and then redirect to **the redirect uri you've specified in developer space** with a `code`

We'll do thing by setting a `Location` header, for example:

`Location: [YOUR REDIRECT URI]?code=theawesomecode`

Or, if you have set multiple `redirect_uri` in the developer space, and you want a specific one to be called:

`[GET] https://cloud.xee.com/v3/auth/auth?client_id=azerty&redirect_uri=https%3A%2F%2Fexample.com%2Fxee%2Foauth`

It will do the same but with

- `https://example.com/xee/oauth` as the `redirect uri`

### The redirect uri

The redirect uri should be owned by you (so either a domain name you own, where you can put some code, either localhost).

When the redirect uri is called, we'll provide you an `access code`, via the parameter `code`.

This code will help you to obtain the first `access token` for the user who signed in.

So keep this code in hand, and then refer to the [access_token](access_token.md) page.

### Errors

If the `client_id` is wrong, or the `redirect_uri` is set but does not match any specified in the [developer space](https://dev.xee.com), we'll throw a `404`

- Reason: `client_id` does not exist or `redirect_uri` is set but does not match
- Status Code: `404`
- Body: An HTML body with
