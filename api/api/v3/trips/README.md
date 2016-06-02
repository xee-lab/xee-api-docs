# Trips

Get the trips data, signals, locations, trips...

> Don't forget the *signals_read*, *locations_read* and *trips_read* scopes.

|API|Information|
|---|---|
|[`/trips/{tripId}`](trip_id.md)|Get a specific *trip*|
|[`/trips/{tripId}/locations`](locations.md)|Get a specific *trip* locations collection|
|[`/trips/{tripId}/locations.geojson`](locations-geojson.md)|Get all locations from a *car* during a specific *trip* in a [geojson](http://geojson.org/) format|
|[`/trips/{tripId}/signals`](signals.md)|Get a specific *trip* signals history|

## Signals list

For the `signals` API, you might want to specify some filters.
See [The list of available signals](../cars/signals_list.md)