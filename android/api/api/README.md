# API Features

`api` contains all the elements you need to _deal with *XeeCloud* APIs_.

## Setup

To use *api*, just add this to your `build.gradle` file

```groovy
dependencies {
    // Xee API
    compile 'com.xee.sdk.v2:api:{lastversion}'
}
```

## Classes List

The *api* module is a bundle of **2 class** which are:

* `XeeApi`
* `XeeAdvancedApi`

## What's the goal ?

We wanted to make the use of *api* simple, so we split our services in 2 categories:

* The common one
* The unusual one

> When you'll make your app. You might need both, but might not. 

If your app is "simple" and does not require complex calls to our APIs, you might be able to build it with only `XeeApi`. 

However, if you need to do *complex requests* like a history of signals on a certain period, you'll need `XeeAdvancedApi`.

## XeeApi

As explained, `XeeApi` has been made for *simple calls* like:

* For the users
	* fetch the currently connected user (using `getCurrentUser`)
	* fetch the phone numbers of a user (using `getPhoneNumbers`)
	* fetch the emails of a user (using `getEmails`)
	* fetch the addresses of a user (using `getAddresses`)
* For the cars
	* fetch the cars for a user (using `getCars`)
* For the devices
	* fetch the devices for a user, like a XeeConnect (using `getDevices`)
* For the data
	* fetch the status of a car (using `getCarStatus`)

> The status of a car is a complete list of the last signals values, plus the last car location, plus the last car accelerometer value.

## XeeAdvancedApi

`XeeAdvancedApi` has been made for *complex api calls* like:

* For the users
	* fetch a specific user with its id (using `getUser`)
	* fetch a specific phone number for a user with its id (using `getPhoneNumber`)
	* fetch a specific email for a user with its id (using `getEmail`)
	* fetch a specific address for a user with its id (using `getAddress`)
* For the cars
	* fetch a specific car for a user with its id (using `getCarFromId`)
	* fetch a specific car connected to a device with its serial number (using `getCarFromDevice`)
* For the devices
	* fetch a specific device for a user with its id (using `getDevice`)
* For the data
	* fetch the history of a list of signals (filtered or not) for a car (using `getCarData`)
	* fetch the history of the locations (filtered or not) for a car (using `getLocationHistory`)
	* fetch the history of the accelerometer values (filtered or not) for a car (using `getAccelerometerHistory`)

### The Filter object

The `Filter` object has been designed to help you filtering the results of your calls when they are made.
For example, you want to access the history of `Locations`

* starting from yesterday
* ending today
* with max 15 values

This is quite a complex call, and if everything was an argument of the method, it would have been a pain to use.
Here the `Filter` enters in.

You just have to build the `Filter` as you want it and give it to the method. In our case the code would be like:

```java
// Build the filter
Filter filter = new Filter()
                    .startOn(yesterDayAsLong)
                    .stopOn(todayAsLong)
                    .withLimit(15);

// Call with it
XeeFuture<List<Location>> locations = XeeAdvancedApi.getLocationHistory(carId, filter, accessToken);
```