# iOS SDK

A complete toolbox for quickstarting Xee development on the iOS Platform.

# Overview

## Installation 

Current version of the *iOS SDK* is `1.1.1`.

If you want to know more about the versions, please check our [Changelog](CHANGELOG.md)

### Cocoa pods

> XeeSDK doesn't work "out of the box", it uses some libraries causing some limitations :
>
> * Needs cocoapods
> * XeeSDK works only on iOS 8 has an embedded library because of PromiseKit v3.

* Install Cocoapods to your project [See how here](https://guides.cocoapods.org/using/getting-started.html)
* Add this to your `podfile` :

```ruby
platform :ios, '8.0'
use_frameworks!

pod 'XeeSDK','~> {lastversion}'
```

## API

See how to use the [iOS SDK](api/README.md)