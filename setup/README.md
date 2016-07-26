# Setup

A guide to setting up your Xee environment

## Create a dev account

In order to create a *developer account*, please go to our [developer space, XeeDEV](https://dev.xee.com) and:

- [Sign in](https://dev.xee.com/login) with your Xee account if you have one
- [Create a Xee account](https://dev.xee.com/register) if you have not

**As simple as that !**

## Create a client for the platform

Once you're connected to our developer space, you can manage your **clients**.

> A client is an "application" that can access our API, it is like a key to the platform.

To get a client, you'll have to fill a form with some basic information:

- Your app name
- An app description
- At least a *redirect_uri* (the URL we'll trigger for the login) 
- A logo url
- The [scopes](scopes.md) you want

You'll get:

- A *client id* which will identify your application on Xee's platform
- A *client secret* which is like the password of your application, keep it safe, we can't get it twice.

And you'll be ready to go :)

## Think about what to do ?

Once you've created your client on the platform, you can go on dealing with our API.
But what is the best to do as we have:

- API
- Android SDK
- iOS SDK

Well, see there

### I want a web app (at least)

In this case, you'll deal with our API directly, you can enjoy our [API Documentation](../api/README.md).

> Note: Be aware of the **redirect_uri** you gave, it should match your domain's name.


### I want a mobile app

Well, thats a good point, but, not an end, the thing is:

*Do you need a third party server ?*

We'll, if you do not know, this is simple, here some example to help you decide:

- if your app will be on more than a system, and you want sync between your servers, then you'll need a third party server.
- if you want to deal with your service on the mobile (not xee's one directly), then you'll need a third party server.
- in fact, as soon as you want the Xee data to be out of the mobile app, you'll need a third party server.

#### I need a third party server

Nice, in this case, this is the same thing for *web app* so you'll deal with our API directly, you can enjoy our [API Documentation](../api/README.md).

> Note: Be aware of the **redirect_uri** you gave, it should match your domain's name.

#### I'll go directly with Xee's API on mobile

##### I'll do this on Android

Great, you'll can either deal with our [API](../api/README.md).
Or you can use the [Android SDK we made for you](../android/README.md)!

> Note: Be aware of the **redirect_uri** you gave, it must be `http://localhost`.

##### I'll do this on iOS

Fantastic, you'll can either deal with our [API](../api/README.md).
Or you can use the [iOS SDK we made for you](../ios/README.md)!

> Note: Be aware of the **redirect_uri** you gave, it must be `http://localhost`.
