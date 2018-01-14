
# Routing APIS

## OSMR - Open Source Routing Machine

[OSMR API](http://project-osrm.org)
[documentation](http://project-osrm.org/docs/v5.10.0/api/#general-options)

Useful features

1. Route service  

Request to  get fastest route between multiple points.
    * Example: 'http://router.project-osrm.org/route/v1/driving/13.388860,52.517037;13.397634,52.529407;13.428555,52.523219?overview=false'
    * Modes: (car, bike, foot)
    * Coordinates: longitude, latitude format (can be multiple)

2. Nearest service

Snaps a coordinate to the street network and returns the nearest n matches.
    * Example: Querying nearest three snapped locations of 13.388860,52.517037 with a bearing between 20° - 340°. 'http://router.project-osrm.org/nearest/v1/driving/13.388860,52.517037?number=3&bearings=0,20'
    * Coordinates: longitude, latitude format (single))

3. Trip service

Traveling Salesman Problem
    * Example: Round trip in Berlin with three stops 'http://router.project-osrm.org/trip/v1/driving/13.388860,52.517037;13.397634,52.529407;13.428555,52.523219'
    * Does not have to be the fastest router
    * Round trip (same origin and destination)/ Non-round trip


**Python example**


```python
from urllib2 import Request, urlopen, URLError
import json
request = Request('http://router.project-osrm.org/route/v1/driving/13.388860,52.517037;13.397634,52.529407;13.428555,52.523219?geometries=geojson&overview=full')

# returns a json object)

try:
	response = urlopen(request)
	data = response.read()
	data_json = json.loads(data)
except URLError, e:
	print 'No data. Got an error code:', e

```

## VROOM - Open Source Routing Machine

* used for optimisation
* based on OSMR

## GRAPHHOPPER

* need an account (free accounts have limitations)

**Python example**

```python
request = Request('https://graphhopper.com/api/1/route?point=51.131,12.414&point=48.224,3.867&vehicle=car&locale=de&key=62cc9e56-ca86-4520-a0f1-7f659847eeb9')

# returns a json object)

try:
 response = urlopen(request)
 data = response.read()
 data_json = json.loads(data)
except URLError, e:
 print 'No data. Got an error code:', e
```
