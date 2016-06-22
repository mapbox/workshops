# Mapbox GL JS Workshop, March 31


![image](https://cloud.githubusercontent.com/assets/4470913/16147933/02ad4360-34a4-11e6-9398-c6ac8092825e.png)

A working prototype of this can be found **[here](http://mapbox.github.io/workshops/mapbox-gl-js/#12.86/12.9774/77.5757)**

---

## Outline
* Introduction
* [Web mapping](https://www.mapbox.com/help/how-web-maps-work/), raster and [vector tiles](https://www.mapbox.com/blog/vector-tiles/), [Web GL](https://www.mapbox.com/blog/mapbox-gl/).
* Workshop
    - Map
    - Bus Stops
    - Nearest Bus Stops
* Break
* Workshop
    - Nearest Bus Stops
    - Bus Stop Reachability
* Closing


## Things we have built with Mapbox GL JS
* [Mapping public transit in Bangalore](https://www.mapbox.com/blog/blr-transit-maps/)
* [Crowdsourcing flood data for Chennai](https://www.mapbox.com/blog/chennai-flood-map/)


## Workshop

### 1. Map

##### Get workshop boilerplate
* Copy the `mapbox-gl-workshop` folder from the flash drive onto your `Desktop`.
* During the workshop we will edit `index.html` inside `mapbox-gl-workshop` folder.
* Open `index.html` in your text editor.


##### Start a web server from the command line
```
python -m SimpleHTTPServer
```


##### Open link in your web browser
[http://localhost:8000/](http://localhost:8000/)


##### Copy [example from GL JS documentation](https://www.mapbox.com/mapbox-gl-js/examples/)
* Copy thw whole example and overwrite the contents of your `index.html` file.


##### Let's give a page title
```
<title>Mapbox GL Workshop</title>
```


##### Include CSS and JS files
```
<link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.16.0/mapbox-gl.css' rel='stylesheet' />
<script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.16.0/mapbox-gl.js'></script>
```

##### HTML div element for the map
```
<div id='map'></div>
```

##### A new [Map](https://www.mapbox.com/mapbox-gl-js/api/#Map) object
```
<script>
mapboxgl.accessToken = '<your access token here>';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'mapbox://styles/mapbox/streets-v8', //stylesheet location
    center: [-74.50, 40], // starting position
    zoom: 9 // starting zoom
});
</script>
```
Access token from Mapbox Account: https://www.mapbox.com/studio/


##### Style for a full screen map
```
<style>
    body { margin:0; padding:0; }
    #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
```


##### Center map on Bengaluru
```
center: [77.5912997, 12.9791198],
```

##### Update initial zoom level
```
zoom: 11,
```

#### Permalink for the map

```
hash: true
```

##### Adding [nagivation control](https://www.mapbox.com/mapbox-gl-js/api/#Navigation)
```
map.addControl(new mapboxgl.Navigation({position: 'top-left'}));
```

### 2. Bus Stops


##### Load bus stop data from [OpenBangalore](http://openbangalore.org/) as [Geojson](http://geojson.org/)
`GeoJSON: Point, LineString, Polygon, MultiPoint, MultiLineString, and MultiPolygon`

```
<script src='data/stops.js'></script>
```


##### Prepare data [soruce](https://www.mapbox.com/mapbox-gl-style-spec/#sources)
`Source: vector, raster, geojson, image, video`

```
var stopsSource = {
    "type": "geojson",
    "data": stops
};
```

##### Create [layer](https://www.mapbox.com/mapbox-gl-style-spec/#layers) using source
`Layers: background, fill, line, symbol, raster, circle`

```
var stopsLayer = {
    "id": "stops",
    "source": "stops",
    "type": "circle",
    "paint": {
        "circle-radius": 2,
        "circle-color": "black",
    },
    "interactive": true
};
```


##### Add source and layer to the map - [Event Listener](https://www.mapbox.com/mapbox-gl-js/api/#Evented.on)
```
map.on('style.load', function () {
    map.addSource("stops", stopsSource);
    map.addLayer(stopsLayer);
});
```


##### Radius of circle [based on zoom](https://www.mapbox.com/mapbox-gl-style-spec/#types-function)
```
"circle-radius": {
    "base": 1,
    "stops": [[8, 1.5], [10, 2], [15, 4], [20, 6]]
},
```


### 3. Nearest Bus Stops


##### On [map click](https://www.mapbox.com/mapbox-gl-js/api/#EventData)
```
map.on('click', function (e) {
    console.log('Map click at: ' + e.lngLat);
});
```


##### Function to show bus stops on map
```
function showStops(e) {

}
```


##### Call function to show stops
```
showStops(e);
```


##### Load the awesome [turf.js](http://turfjs.org/)
```
<script src='https://api.tiles.mapbox.com/mapbox.js/plugins/turf/v2.0.0/turf.min.js'></script>
```


##### Create a [circular](https://www.dropbox.com/s/sgzp010kbc612lt/circle-on-earth.png?dl=0) [buffer](http://turfjs.org/static/docs/module-turf_buffer.html)
```
var point = turf.point([e.lngLat.lng, e.lngLat.lat]);
var buffer = turf.buffer(point, 1, 'kilometers');
```


##### Buffer source
```
var bufferSource = {
    "type": "geojson",
    "data": buffer
};
```


##### Buffer layer
```
var bufferLayer = {
    "id": "buffer",
    "source": "buffer",
    "type": "fill",
    "paint": {
        "fill-color": "black",
        "fill-opacity": 0.1
    }
};
```


##### Add source and layer dynamically on click
```
map.addSource("buffer", bufferSource);
map.addLayer(bufferLayer);
```


##### Function to remove unused layers
```
function clear() {
    if (map.getLayer('buffer')) {
        map.removeLayer('buffer');
        map.removeSource('buffer');
    }
}
```


##### Remove unused layers before processing click
```
clear();
```


##### Find stops within buffer
```
findStops(buffer);
```


##### Function to find stops [within](http://turfjs.org/static/docs/module-turf_within.html) buffer
```
function findStops(buffer) {
    var stopsWithin = turf.within(stops, buffer);
    console.log('Number of stops within: ' + stopsWithin.features.length);
}
```


##### New layer for stops within
[Paint properties](https://www.mapbox.com/mapbox-gl-style-spec/#layers)
```
var stopsWithinLayer = {
    "id": "stopsWithin",
    "source": "stops",
    "type": "circle",
    "paint": {
        "circle-radius": 20,
        "circle-color": "red",
        "circle-opacity": 0.6,
        "circle-blur": 0.8
    },
    "filter": ["==", "name", ""]
};
```


##### Add stops within layer to map
```
map.addLayer(stopsWithinLayer);
```


##### [Filters!](https://www.mapbox.com/mapbox-gl-style-spec/#types-filter) Filter out stops within
```
var filters = ["any"];
stopsWithin.features.forEach(function(stop) {
    filters.push(["==", "name", stop.properties.name]);
});
map.setFilter("stopsWithin", filters);
```


##### Cleanup
```
map.setFilter("stopsWithin", ["==", "name", ""]);
```

##### Including jQuery
```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js"></script>
```

##### Block to display stop names.
```
<div id='info'>
    <ul id='stoplist'></ul>
</div>
```

##### Styling stop names block
```
#info { z-index: 1; position: absolute; top: 10px; right: 10px; background-color: #fff;}
```


##### Access stop list
```
var stopList = $('#stoplist');
```

##### Append names to the list
```
var li = $('<li/>').appendTo(stopList);
var entry = $('<span/>').text(stop.properties.name.split(',')[0]).appendTo(li);
```


##### Cleanup names
```
$('li').remove();
```


### 4. Bus Stop Reachability

##### Add destinations
```
<script src='data/destinations.js'></script>
```

##### Add destination source
```
var destinationsSource = {
    "type": "geojson",
    "data": destinations
};
```

##### Add destination layer
```
var destinationsLayer = {
    "id": "destinations",
    "type": "line",
    "source": "destinations",
    "layout": {
        "line-join": "round",
        "line-cap": "round"
    },
    "paint": {
        "line-color": "black",
        "line-width": 1,
        "line-opacity": 0.8,
        "line-blur": 1
    },
    "filter": ["==", "name", ""]
};
```

##### Add destination source and layer to map
```
map.addSource("destinations", destinationsSource);
map.addLayer(destinationsLayer);
```

##### Query features on button click with [queryRenderedFeatures](https://www.mapbox.com/mapbox-gl-js/api/#Map.queryRenderedFeatures)
```
var x1y1 = [e.point.x - 5, e.point.y - 5];
var x2y2 = [e.point.x + 5, e.point.y + 5];
var clickedFeatures = map.queryRenderedFeatures([x1y1, x2y2], { layers: ["stops"] });
```

##### Display bus stops you can travel to
```
if (clickedFeatures.length) {
    clear();
    map.setFilter("stopsWithin", ["==", "name", clickedFeatures[0].properties.name]);
    map.setFilter("destinations", ["==", "name", clickedFeatures[0].properties.name]);
} else {
    showStops(e);
}
```

##### Cleanup destination layer
```
map.setFilter("destinations", ["==", "name", ""]);
```

### 5. Bus Route Labels

##### Create a route label layer
```
var routeLabel = {
    "id": "routeLabel",
    "type": "symbol",
    "source": "destinations",
    "layout": {
        "symbol-placement": "line",
        "text-field": "{route}",
        "text-size": 12,
        "text-offset": [0, 1]
    },
    "paint": {
        "text-halo-color": "red",
        "text-halo-width": 0.2
    },
    "filter": ["==", "name", ""]
};
```

##### Add layer to map
```
map.addLayer(routeLabel);
```

##### Set filter to display labels
```
map.setFilter("routeLabel", ["==", "name", clickedFeatures[0].properties.name]);
```

##### Cleanup route labels
```
map.setFilter("routeLabel", ["==", "name", ""]);
```
