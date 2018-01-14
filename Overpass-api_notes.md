## Draft doc for using OSM-api python wrapper

### 1.0 introduction
We describe here some OSM-api services and to select an appropriate one for usage in the web-app.
The OSM-api service should be used for both visualisation and for routing purposes.
There are generally two types of web-framework we can use to get the OSM data. This includes
lower-level ones that downloads the data and higher-level ones that immediately embeds
into web-pages. Description of the different frameworks can be found in the link below.
reference: https://wiki.openstreetmap.org/wiki/Frameworks#Webmaps


### 2.0 Overpass (read-only optimised API that collect OSM data)
we document here how to use overpass api in python. The Overpass API (aka OSM Server Side) is a read-only API that serves custom OSM map data. It is a web-database where the client can sends a request to the API for selected data. For more information please see: https://wiki.openstreetmap.org/wiki/Overpass_API

We will test here two different thin wrappers for OSM-API in python.
One is called overpy and another is called overpass


### 2.1 Example Scripts for overpy

https://github.com/DinoTools/python-overpy

```
pip install overpy
```

simple get functions

```python
import overpy

api = overpy.Overpass()

# fetch all ways and nodes
result = api.query("""
    way(50.746,7.154,50.748,7.157) ["highway"];
    (._;>;);
    out body;
    """)

for way in result.ways:
    print("Name: %s" % way.tags.get("name", "n/a"))
    print("  Highway: %s" % way.tags.get("highway", "n/a"))
    print("  Nodes:")
    for node in way.nodes:
        print("    Lat: %f, Lon: %f" % (node.lat, node.lon))

```


### 2.2 Example Scripts for overpass

https://github.com/mvexel/overpass-api-python-wrapper

```
pip install overpass
```

using bounding box to retrieve OSM data

 ```python

 import overpass
 # Cambridge, UK bounding box coordinates
 # 0.0686, 52.1579, 0.1885, 52.2370
 min_long = 0.0686
 min_lat = 52.1579
 max_long = 0.1885
 max_lat = 52.2370

 # query overpass within OpenStreetMap
 api = overpass.API()
 #response = api.Get('node["name"="Oxford"]')
 map_query = overpass.MapQuery(min_lat,min_long,max_lat,max_long)
 response = api.Get(map_query)

 ```
