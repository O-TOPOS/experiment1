## Meeting Notes - 14/01/2018

### OTOPOS-Travelling-app

1. definition of project
- Our aim is to create a simple web-app which takes an input 'origin', 'destination'
and it outputs a route based on Points of interests ('POI')
- the Web-app will visualise the map and has a basic UI that allows for simple
'origin' and 'destination' form boxes.
- we will experiment with different cloud-services rather than any static libraries.
- the first development version of the web-app will download the map tile of the origin and destination using OSM-api and then to find the route using OSM-routing-api.

2. Initialisation steps
- LV will develop the basic steps to create a unified Django framework and local
server with the same settings, modules and libraries. This ensures we can replicate
any of the research in our local machines locally.
- IK will develop the basic protocols and workflow for the project. This includes
first cloning the repo locally, creating a branch in git-desktop and make sure all
changes are merged back with the master-branch in a pull requests.

3. Initial research
- The objective of this initial research is to select the key services to use
for the web-app
- we will conduct initial research on using OSM-API and OSM-routing-API.
- This includes basic descriptions and snippets on using these selected API.
- We should begin by simply visualising the maps and being able to produce routing
between 'origin' and 'destination' using simple API and without any UI.

4. Future research
- we will conduct User-interaction (UI) research at a future stage.
- we might develop our own routing functions if the functions don't exist in
existing routing-api.
