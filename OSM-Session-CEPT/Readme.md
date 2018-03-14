## OpenStreetMap - Contribute, extract, analyse and visualise


**8th of March** | **[Centre for Environmental Planning and Technology](http://cept.ac.in/), Ahmedabad, India**

[Jinal Foflia](https://in.linkedin.com/in/jinalfoflia) - jinal@mapbox.com | [@fofliajinal](https://twitter.com/fofliajinal)

----

### Contribute

#### Getting started with OpenStreetMap

- Sign up [here](https://www.openstreetmap.org/), if you are just getting started with OpenStreetMap

- Introduction to `node(point)`, `way(line)`, and `area(closed polygon)`.

![pasted image at 2017_07_20 10_19 pm](https://user-images.githubusercontent.com/6770741/28456397-c7b56830-6e1f-11e7-9404-3838bfbcbd9e.png)
- How to map buildings. For more: https://www.mapbox.com/mapping/


##### Highway classification

Roads are added with the tag `highway=*`
- Residential roads `highway=residential` - http://wiki.openstreetmap.org/wiki/Tag:highway%3Dresidential
- Service roads  `highway=service` - http://wiki.openstreetmap.org/wiki/Tag:highway%3Dservice
- Paths `highway=path` - http://wiki.openstreetmap.org/wiki/Tag:highway%3Dpath
- Unclassified road`highway=unclassified` - http://wiki.openstreetmap.org/wiki/Tag:highway%3Dunclassified

### Extract

[Overpass turbo](http://overpass-turbo.eu) is a web based [data mining (extracting) tool](https://wiki.openstreetmap.org/wiki/Overpass_turbo) for OpenStreetMap. The source code is found [on github](https://github.com/tyrasd/overpass-turbo). 
 
- Here are the [frequently used](https://github.com/mapbox/mapping/wiki/Overpass:-Frequently-used-queries) overpass queries ([Overpass API/Overpass API by Example
](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example))
- Overpass query that we used during the session - https://overpass to extract bus stops in Ahmedabad - turbo.eu/s/wNT
- [Overpass API](https://wiki.openstreetmap.org/wiki/Overpass_API) is a read-only API that serves up custom selected parts of the OSM map data.


### Analyse

- [Spatial analysis](https://www.mapbox.com/help/how-analysis-works/) - Spatial analysis includes a variety of techniques and processes used to understand the patterns and relationships of geographic features. Turf, an open source project maintained by Mapbox, is an advanced geospatial JavaScript library that allows you to perform spatial operations in the browser.
- [Turf.js](http://turfjs.org/) - Turf.js is a JavaScript library for spatial analysis. It includes traditional spatial operations, helper functions for creating GeoJSON data, and data classification and statistics tools. Turf can be added to your website as a client-side plugin, or you can [run Turf server-side](https://www.npmjs.com/package/turf) with [Node.js](http://nodejs.org/). You can find the source code on [GitHub](https://github.com/turfjs/turf).
- [Analyze data with Turf.js and Mapbox GL JS](https://www.mapbox.com/help/analysis-with-turf/) - This guide walks through the basics of Turf.js, a JavaScript library used for spatial analysis and statistics, and how to use it to add spatial analysis to your Mapbox GL JS maps.
- [QGIS](https://en.wikipedia.org/wiki/QGIS) - QGIS is a free and open-source cross-platform desktop geographic information system application that supports viewing, editing, and analysis of geospatial data. Find various [tutorials](https://www.qgistutorials.com/en/) related to using QGIS

### Visualise

[Mapbox Studio](https://www.mapbox.com/studio) is your home base for building custom maps with Mapbox. [This manual](https://www.mapbox.com/help/studio-manual/) contains information on how Mapbox Studio works, some guidance on best practices, and a comprehensive application reference.

To get started, you'll only need to sign up to a Mapbox account at [Mapbox.com](https://www.mapbox.com/).


Here are few tutorials from our previous workshops that you can refer to 

- [Webinar: Introduction to Mapbox Studio](https://github.com/mapbox/workshops/tree/gh-pages/HOT-webinar-2017)
- [Workshop: Designing custom maps for your brand](https://github.com/mapbox/workshops/tree/gh-pages/branding-workshop)
- [Futuristic Map Design workshop at Dfrost 2017](https://github.com/mapbox/workshops/tree/gh-pages/dfrost-2017-scifi-map)
 

### Other interesting projects that's used either of the above

- POI finder - https://oini.github.io/poi-finder/
- Chennai Flood Maps - https://osm-in.github.io/flood-map/chennai.html#11.65/13.0493/80.2593
- Railway map - https://shvrm.github.io/railway/#11/50.8783/-355.6201
- Analysis - https://www.townsendjennings.com/maps/
- More about OpenStreetMap - learnosm.org/en/

Find tutorials, answers to your questions on Mapbox's [help page](https://www.mapbox.com/help/#glossary) and feel free to reach out to us on [Twitter](https://twitter.com/Mapbox) or follow our [FB page](https://www.facebook.com/Mapboxblr/).

State of the Map Asia is happening in November 2018, follow the [Twitter account](https://twitter.com/SotmAsia) for more information and updates
