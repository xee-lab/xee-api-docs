# Auth Features

`auth` contains all the elements you need to _authenticate the user_.

## Setup

To use *auth*, just add this to your `build.gradle` file

```groovy
dependencies {
    compile 'com.xee.sdk.v2:auth:{lastversion}'
}
```

## Classes List

The *core* module is a **single class** which is `XeeAuth`

## What it does

`XeeAuth` provides you the help you need to:

* Authenticate a user
* Refresh the _access token_

As we are using *OAuth2*, the _access token_ is the *key* of every data on _XeeCloud_.

If you try to access a data with an obsolete _access token_ you'll get a *403*.

If you get that, you'll have to refresh the token.


### Authenticate the user

First step for you will be the *User authentication*.

User authentication is simple, in fact you just have to do something like that in your _Starter Activity_: 

```java
@Override
public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    if(!hasUserAlreadyAuthenticatedHimself()){
        // User has never authenticated himself
        XeeAuth.authenticateUser(this, new XeeAuth.Callback(){

            public void onUserAuthenticated(final XeeAuth.Token token){
                tokenRefreshed(token);
            }

            public void onError(final Throwable error){
                refreshTokenError(error);
            }

        });
    } else {
        // User has already authenticated himself, refresh its token (see below)
    }
}

/**
 * Store the token and go on
 */
private void tokenRefreshed(final Auth.Token token){
    // Store the token and go on
    yourstorage.storeToken(token);
}

/**
 * Error while authenticating user / refreshing token
 */
private void refreshTokenError(final Throwable error) {
    // Deal with the error
}

/**
 * This method checks in your storage if any token (refresh token, access token, ..) is stored.
 * If there is one, then the user has authenticated himself, if not, you'll need to authenticate him
 * @return true if there is a token in the storage, false otherwise
 */
private boolean hasUserAlreadyAuthenticatedHimself(){
    // Check by yourself in your storage for a token
    return yourstorage.hasToken();
}
```


### Refresh the token

To refresh a token, edit your _Starter Activity_ just like that: 

```java
@Override
public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    if(!hasUserAlreadyAuthenticatedHimself()){
        // User has never authenticated himself, (see above)
    } else {
        // User has already authenticated himself, refresh its token
        XeeAuth
            .refreshAccessToken("refresh_token")
            .addListener(new XeeFuture.XeeListener<XeeAuth.Token>() {

                public void onSuccess(final XeeAuth.Token token) {
                    tokenRefreshed(token);
                }

                public void onError(final Throwable error){
                    refreshTokenError(error);
                }

            }, Executors.newSingleThreadExecutor());
    }
}
```

Here we are, the *Authentication* is done.


> If you need to *refresh the token* latter, just use `XeeAuth.refreshAccessToken()` like we just did there.

> Here, we used a callback system within the _Activity_, but the return of `XeeAuth.refreshAccessToken()` is a *Future*, so you can put everything in a _Manager_