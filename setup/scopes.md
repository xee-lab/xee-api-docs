# Scopes

Make a whish, get a scope

## What is a scope

A *scope* is like an authorization to get a *specific resource*.

For example, at Xee we provide different things:

- User info
- Car info
- Signals data (from a Car)
- Trips
- Locations
- ... A lot more

If you build an app that does not need to access *trips*, then, why should you need to access it ?
You just don't. So we wont provide your app the resource, even if you try to *call the API*

Right, at this point, some of you might be like:

> Wait, why wouldn't I ask for every scopes ? I does not cost anything, even if I don't call the API

You're right.. You might, but be aware our authentication system will **show the user** every *scope* you're asking for. So, asking more than needed might not be the right thing to do.

## What are the scopes provided by Xee

| Data you want | API that provide | scope needed |
|---|---|---|
|Read user info| [`/users/me`](../api/api/v3/users/me.md)<br /> [`/users/{userId}`](../api/api/v3/users/user_id.md) | *users_read* |
|Read car info| [`/users/{userId}/cars`](../api/api/v3/users/cars.md)<br /> [`/cars/{carId}`](../api/api/v3/cars/car_id.md) | *cars_read*|
|Get car trips| [`/cars/{carId}/trips`](../api/api/v3/cars/trips.md)<br /> [`/trips/{tripId}`](../api/api/v3/trips/trip_id.md) | *trips_read*|
|Get signals from car| [`/cars/{carId}/signals`](../api/api/v3/cars/signals.md)<br /> [`/trips/{tripId}/signals`](../api/api/v3/trips/signals.md) | *signals_read*|
|Get locations from car| [`/cars/{carId}/locations`](../api/api/v3/cars/locations.md)<br /> [`/trips/{tripId}/locations`](../api/api/v3/trips/locations.md) | *locations_read*|
|Get status of a car| [`/cars/{carId}/status`](../api/api/v3/cars/status.md) | *status_read*|


