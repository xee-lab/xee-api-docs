# Cars

Get car data, signals, locations, trips...

> Don't forget the *signals_read*, *accelerometers_read*, *trips_read*, *locations_read* and *status_read* scopes.

|API|Description|
|---|---|
|[`/cars/{carId}`](car_id.md)|Get a specific car from its *id*|
|[`/cars/{carId}/status`](status.md)|Get the last status of the car|
|[`/cars/{carId}/locations`](locations.md)|Get raw locations history of the car|
|[`/cars/{carId}/locations.geojson`](locations-geojson.md)|Get car *locations* history in a [geojson](http://geojson.org/) format|
|[`/cars/{carId}/signals`](signals.md)|Get raw signals history of the car|
|[`/cars/{carId}/trips`](trips.md)|Get the car *trips*|

## Signals list

For the `signals` API, you might want to specify some filters.
See [The list of available signals](signals_list.md)