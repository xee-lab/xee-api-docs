## API overview

Theses classes are required to initialize the SDK :

- `XEE`
- `XEEClient`
- `XEEEnvironment`

> Those 3 classes are the base of a *Xee* application. You'll need to init them before doing anything.

* 1st step: Initialize the `XEEClient` with the data you receive on [app creation](../../setup/README.md)

Add this in your `AppDelegate.m`

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    XEEClient *client = [[XEEClient  alloc] init];
    client.clientId = XEE_CLIENT_ID;
    client.password = XEE_PASSWORD;
    client.callbackUri = @"http://localhost";
    client.scopes = XEE_SCOPE;
    client.environment = XEEEnvironmentProd;
}
```

* 2nd step: Setup the `XEE` singleton. It is used by the *SDK*.

Add this in your `AppDelegate.m`

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    XEEClient *client = [[XEEClient  alloc] init];
    /*show previous chapter...*/

    [XEE setup:client];
}
```

Here we are, the *SDK* is initialized

### Auth Features

This chapter contains all the elements you need to _authenticate the user_.

#### Classes List

The *core* module is architectured in a **single class** which is `XEEAuth`

### What it does

`XEEAuth` provides you the help you need to:

* Authenticate a user
* Refresh the _access token_

As we are using *OAuth2*, the _access token_ is the *key* of every data on _XeeCloud_. +
If you try to access a data with an obsolete _access token_ you'll get a *403*. +
If you get that, you'll have to refresh the token.

#### Authenticate the user

First step for you will be the *User authentication*.

User authentication is simple, in fact you just have to do something like that in your `ConnectionViewController.m`

```objective-c
- (void)viewDidAppear:(BOOL)animated {
    [super viewDidAppear:animated];

    if([self token] == nil){
        // User has never authenticated himself
       [XEEAuthentication authenticateWithHostViewController:self andDelegate:self];
    } else {
        // User has already authenticated himself, refresh its token (see below)
    }
}

/*
* User succeful authenticated ! Let's store his token
*/
- (void)success:(XEEToken *)token {
    [self setToken:token];
}

/*
* Oops, error occured
*/
- (void)error:(NSError *)error {
    NSLog(@"Failed to connect user, error : %@", error);
}

/*
* User cancel connection
*/
- (void)cancel {
    NSLog(@"User cancel connection");
}

/*
* Save my token
*/
- (XEEToken *) token {
    return [self.myStorage token];
}

/*
* Retreive my token
*/
- (void) setToken:(XEEToken *) token {
    [self.myStorage saveToken:token];
}
```


#### Refresh the token

To refresh a token, edit your `ConnectionViewController.m` just like that: 

```objective-c
- (void)viewDidAppear:(BOOL)animated {
    [super viewDidAppear:animated];

    if([self token] == nil){
        // User has never authenticated himself
       [XEEAuthentication authenticateWithHostViewController:self andDelegate:self];
    } else {
        [XEEAuthentication refreshToken:[self token].refreshToken].then(^(XEEToken *newToken) {
            [self setToken:newToken];
        }).catch(^(NSError *error) {
            NSLog(@"Failed to refresh token, error : %@", error);
        });
    }
}
```

Here we are, the *Authentication* is done.



