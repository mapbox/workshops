# Comparing vegetation cover using Landsat

This tutorial uses a command line tool called [landsat-util](https://pythonhosted.org/landsat-util/) to download and process the infrared satellite imagery of a place at two different time intrevals and compare them in qgis. We will compare the vegetation loss over the Indian city of [Vishakapatnam]() after [cyclone Hudhud](https://en.wikipedia.org/wiki/Cyclone_Hudhud) destroyed most of the city's tree cover.

## Setup

- Install [landsat-util](https://pythonhosted.org/landsat-util/installation.html). Requires python.
- Install [qgis](https://www.qgis.org)

## Find the imagery 

- Use https://remotepixel.ca/projects/satellitesearch.html to browse to Vishakapatnam 
- Open the latest image in the sidebar and shortlist the scene ids of the imagery with minimum cloud cover in the focus area before and after the cyclone (October 2014) eg. before: `LC81410482014085LGN00` after:`LC81410482015056LGN00`

## Download the imagery
- In terminal runt he command `landsat download LC81410482014085LGN00 LC81410482015056LGN00 --bands 543`
