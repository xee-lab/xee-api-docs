# Changelog

## v3

|Date|Type|Description|Link|
|---|---|---|---|
|2016-09-05|UPDATE|Fixes a typo (issue #38)|[`/users/{userId}`](api/v3/users/user_id.md), <br />[`/users/me`](api/v3/users/me.md)|
|2016-08-25|UPDATE|The parameter `inservice` was replaced by `in_service`|[`/ktype/{ktype}`](compat/v1/ktype/ktype.md)
|2016-08-01|ADD|Add compatibility API|[`/compat/v1`](compat/v1/README.md)|
|2016-07-27|UPDATE|Typo in stats|[`/cars/{carId}/stats/usedtime`](api/v3/cars/stats/usedtime.md)|
|2016-07-25|UPDATE|Fixes a typo (issue #26)|[README](api/v3/README.md)|
|2016-07-15|ADD|Add `cars` stats|[`/cars/{carId}/stats/mileage`](api/v3/cars/stats/mileage.md),<br />[`/cars/{carId}/stats/usedtime`](api/v3/cars/stats/usedtime.md)|
|2016-07-07|UPDATE|Update `trips` responses|[`/cars/{carId}/trips`](api/v3/cars/trips.md),<br />[`/trips/{tripId}`](api/v3/trips/trip_id.md)|
|2016-06-27|ADD|We've added *sandbox* APIs on specified routes|[`/users/{userId}`](api/v3/users/user_id.md), <br/>[`/cars/{carId}`](api/v3/cars/car_id.md),  <br/>[`/cars/{carId}/locations`](api/v3/cars/locations.md), <br/>[`/cars/{carId}/locations.geojson`](api/v3/cars/locations-geojson.md), <br/>[`/cars/{carId}/signals`](api/v3/cars/signals.md), <br/>[`/cars/{carId}/status`](api/v3/cars/status.md), <br/>[`/cars/{carId}/trips`](api/v3/cars/trips.md), <br/>[`/trips/{tripId}`](api/v3/trips/trip_id.md), <br/>[`/trips/{tripId}/locations`](api/v3/trips/locations.md), <br/>[`/trips/{tripId}/locations.geojson`](api/v3/trips/locations-geojson.md), <br/>[`/trips/{tripId}/signals`](api/v3/trips/signals.md)|
|2016-05-23|UPDATE|The parameters `redirect_uri` and `scope` are not mandatory anymore|[`/auth/auth`](api/v3/auth/auth.md)|
|2016-05-22|UPDATE|Complement error cases|[`Authentication README`](api/v3/auth/README.md)
|2016-05-12|ADD|We've added a `/users/me/cars` route|[`/users/me/cars`](api/v3/users/me/cars.md)|
|2016-05-12|ADD|We've added a `/users/me/cars` route|[`/users/me/cars`](api/v3/users/me/cars.md)|
|2016-05-12|UPDATE|The field `deviceId` in *cars* entity is now a `string`|[`/users/{userId}/cars`](api/v3/users/cars.md), <br/>[`/cars/{carId}`](api/v3/cars/car_id.md)|
