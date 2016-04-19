# Android SDK

A complete toolbox for quickstarting Xee development on the Android Platform.

## Installation 

Current version of the *Android SDK* is `1.1.1`.

If you want to know more about the versions, please check our [Changelog](CHANGELOG.md)

### Gradle

We recommend installing with [Gradle](https://gradle.org). This will automatically install the necessary dependencies and pull the SDK binaries.

> For now, the Android SDK is hosted in our private repository, but it might change one day.

To install the current **stable** version, add this to your root `build.gradle` file

```groovy
repositories {
    maven {
    	url 'https://developer.xee.com/android/sdk'
    }
    // ------------------
    // Some repos, fe. jcenter()
    // ------------------
}
```

With this, the *gradle* system will be able to find the parts available of our SDK.

Then, you can add the *dependencies* needed to the *module* you want them, just by adding them to the module's `build.gradle` file

For example:

```groovy
dependencies {
	compile 'com.xee.sdk.v2:commons:{last_version}'
	compile 'com.xee.sdk.v2:auth:{last_version}'
	compile 'com.xee.sdk.v2:api:{last_version}'
}
```

> The `commons` dependency is included in all the others dependencies so it will be included automatically.


## API overview

We assume you have a Java IDE (like Android Studio) with the Android SDK installed, an application project open, and the *Xee Adroid SDK* included as *dependency*.

The SDK needs an Internet connection so it has permissions in its `AndroidManifest.xml`

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
```

### Commons

The `commons` dependency contains all the "entity" *classes*, like a `Car`, a `User` or a `Signal`.
Please read the [Commons README](api/commons/README.md) for more.


### Auth

The `auth` dependency helps you with the *user authentication* and the *token management*.
Please read the [Auth README](api/auth/README.md) for more.


### API

The `api` dependency helps you deal with our API, XeeCLOUD, it does all the calls and error management for you.
Please read the [API README](api/api/README.md) for more.


 


