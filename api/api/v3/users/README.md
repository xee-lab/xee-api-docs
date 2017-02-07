# Users

Get the logged in user information.

> Don't forget the *users_read* and the *cars_read* scopes.

|Method|API|Description|
|---|---|---|
|GET|[`/users/me`](me.md)|Get the connected user|
|GET|[`/users/{userId}`](user_id.md)|Get a specific user|
|GET|[`/users/{userId}/cars`](cars.md)|Get all the cars from a user|
|POST|[`/users/{userId}/cars`](cars.md)|Create a car for this user|