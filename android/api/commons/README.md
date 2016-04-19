# Commons

`commons` contains all the elements you need to use the SDK.

## Setup

To use *commons*, just add this to your `build.gradle` file

```groovy
dependencies {
    compile 'com.xee.sdk.v2:commons:{lastversion}'
}
```

## Classes List

The *commons* module is a bundle of classes, grouped in different _packages_

- car
- data
- user

And some other useful classes.

## Initialize the SDK

The root package contains 3 classes.

- `Xee`
- `XeeClient`
- `XeeEnvironment`

>Those 3 classes are the base of a *Xee* application. You'll need to init them before doing anything.

---

* 1st step: Initialize the `XeeClient` with the data you received with the [app creation](../../setup/README.md)

```java
@Override
public void onCreate() {
    super.onCreate();

    // 1st, init the client
    XeeClient client = new XeeClient(
        "your client id",                           // Client Id of the app
        "your client secret",                       // Client Secret of the app
        Arrays.asList("your scopes", "as list"),    // Scopes are strings passed as List
        "your client name",                         // The client name might be empty
        "http://localhost",                         // The redirect uri on mobile is http://localhost
        XeeEnvironment.Production                   // The environment can be Staging
    );
}
```

* 2nd step: Initialize the `Xee` singleton. It is used within the other *modules*

```java
@Override
public void onCreate() {
    super.onCreate();

    // 1st, init the client
    XeeClient client = new XeeClient( ... );

    // 2nd, init Xee
    Xee.init(client):
}
```

Here we are, the *SDK* is initialized

## Moreover

> In order to make your life easier, all classes in the `commons` module are _Parcelable_.