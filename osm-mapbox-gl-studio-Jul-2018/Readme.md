# [OSM + Mapbox GL JS + Mapbox Studio workshop](https://2018.stateofthemap.org/2018/W017-Building_your_OSM_web_app_in_minutes_with_vector_tiles/
)

## **Getting started**

We’ll use [OverpassTurbo](http://overpass-turbo.eu/) to extract OSM data, style it in Mapbox Studio, and then use an open platform to create an interactive demo.

You’ll only need to sign up to a Mapbox account at [Mapbox.com](https://www.mapbox.com/studio/signup/).


## **Final result**

An interactive demo


## **Finding a theme**

Most often, you would have a dataset (in the form of a .csv, .geojson or other common geo-based data formats). For this workshop, we’ll start from scratch, and use data from OpenStreetMap.
Find a particular type of data (OSM tags) you want to use. We’ll use bus stops in Milan, details of which can be found on the [OSM wiki page](http://wiki.osm.org/) for [bus stops](https://wiki.openstreetmap.org/wiki/Tag:highway%3Dbus_stop).

These are defined as `[highway](https://wiki.openstreetmap.org/wiki/Key:highway)``=``**bus_stop**`


## **Extracting** **small** **data from OSM**

We’ll use [Overpass Turbo](https://overpass-turbo.eu/), that can allow us to zoom to a particular area on the map, and query for specific OSM features.

We can start by zooming in to Milan (or searching for Milan), and using the `Wizard` option to create queries:

- Start with `highway="bus_stop"` ([Result](https://overpass-turbo.eu/s/Az2))
- We can restrict the search to a location (city, country etc.) — Try using `highway="bus_stop" in "Milan"` ([Result](https://overpass-turbo.eu/s/Az4))
- We can export this data as a `geojson` so we can use this in [Mapbox Studio](https://www.mapbox.com/studio/signup/)

Tip: For complex queries, here’s a [quick introductory guide](https://github.com/mapbox/mapping/wiki/Overpass-Guide) and list of [commonly used queries](https://github.com/mapbox/mapping/wiki/Overpass:-Frequently-used-queries).

![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532813103332_overpass_turbo.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532813208282_overpass_turbo.png)



## Extracting big data from OSM

If you are more comfortable with using the command line and want to query more data that you can export from Overpass you can follow this section, otherwise please skip.
This is only possible to follow along if you are using OSX or are an experienced Linux user.

Go to [Geofabrik extracts](https://download.geofabrik.de/europe.html) and download an OSM PBF extract. Use a small extract for this workshop to avoid high WiFi usage. You can apply the same techniques on a global scale however!

![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532614715928_Banners_and_Alerts_and_Geofabrik_Download_Server_and_Slack_-_Mapbox.png)


Install [Osmium Tool](https://osmcode.org/osmium-tool/). This can be tricky for Linux distributions but for OSX you just have to `brew install osmium-tool`. 


Using the [osmium tags-filter command](https://docs.osmcode.org/osmium/latest/osmium-tags-filter.html) you can filter the OSM PBF down to the data you want to include.

```bash
    osmium tags-filter --output ./cyprus-latest.bus_stop.osm.pbf ./cyprus-latest.osm.pbf 'n/highway=bus_stop'
```

Using the [osmium export command](https://docs.osmcode.org/osmium/latest/osmium-export.html) you can turn the OSM PBF into a GeoJSON or a line delimited GeoJSON file.

```bash
    osmium export ./cyprus-latest.bus_stop.osm.pbf \
      -f geojsonseq \
      --omit-rs > cyprus_bus_stops.ld.geojson
```

Mapbox Studio can create vector tiles for you from nearly any GIS format.
However you can also create vector tiles yourself locally using tippecanoe.

Install [tippecanoe](https://github.com/mapbox/tippecanoe) with `brew install tippecanoe`. 

```bash
    tippecanoe \
      -f ./cyprus_bus_stops.ld.geojson \
      -o ./cyprus_bus_stations.mbtiles \
      -zg --drop-densest-as-needed \
      -l bus_stations
```

Now upload the `cyprus_bus_stations.mbtiles` as a new tileset in Mapbox Studio.

## **Adding data to Mapbox Studio**


![](https://d2mxuefqeaa7sj.cloudfront.net/s_FEF097A6C80381F018305649D9F631278657AD25D5290AE115FD1A35C0EFA524_1532601308681_image.png)


Next, we’ll open [Mapbox Studio](https://www.mapbox.com/studio/). If you want to have an editable copy of the dataset, or want to create a dataset from scratch, you can use the Dataset Editor to create the dataset, and then export that as a tileset. In this case, we don’t want to edit the data, so we’ll directly create a tileset with this data by uploading it.
Tip: You can read more about when to use Dataset Editor and when to directly use Tilesets in this [Mapbox Manual guide](https://www.mapbox.com/help/studio-manual-uploads/).


## **Styling the data**

With the tileset ready, we’ll add it to a new map style.

- Click `Add to style` on the tileset page
- Give the style a name (like `Bus stops in Milan`) and select `Basic` template
- In the `New layer` panel, select `Circle` and `Create layer`
- Play with the style properties, and with other layers
    Circle works well for only nodes. In this case, we notice that polygons (like buildings) are shown as multiple circles, which isn’t what we want.
- Select your layer, and go to `Select data` tab
- Switch the layer type to `Symbol` (T)
- Click the `Style` tab to see more style properties you can edit now
- In the `Icon` tab, pick an icon (`bus-11`)
- Explore other properties, such as `Allow icon overlap` in `Placement` tab


![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532813628914_Milano_Bus_Stops___Mapbox_and_Slack_-_Mapbox.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532814200084_Milano_Bus_Stops___Mapbox.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532814589849_Milano_Bus_Stops___Mapbox.png)



## **Publishing the map style**


![](https://www.dropbox.com/s/677wtiue4tbogeg/Screenshot%202018-07-26%2016.11.29.png?raw=1)


Once we’re happy with the style, we can `Publish` the style so it can be shared with others, or used for building more interactive maps.

- Click `Publish`, and review the changes
- Once published, click on the `eye` icon to preview your map style
- Notice the `Style URL` and `Access token`: these are used to link to your map style and specify your user credentials when you use this in any application


## Embed your map in an HTML page

We are following parts of https://www.mapbox.com/help/add-points-pt-3/.

We create an HTML page.

```html
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset='utf-8' />
        <title>Build a map with Mapbox GL JS at SOTM2018</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.46.0/mapbox-gl.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.46.0/mapbox-gl.css' rel='stylesheet' />
        <style>
          body { margin: 0; padding: 0; }
          #map { position: absolute; top: 0; bottom: 0; width: 100%; }
        </style>
      </head>
      <body>
        <div id='map'></div>
        <script>
        mapboxgl.accessToken = 'pk.eyXX'; // replace this with your access token
        var map = new mapboxgl.Map({
          container: 'map',
          style: 'your-style-URL-here', // replace this with your style URL
          hash: true
        });
        // code from the next step will go here
        </script>
      </body>
    </html>
```

If we open that HTML page you should now see your map.

## **Adding interactivity**

We are going to add a little Popup that shows the `name` , `ref`, and `operator` of the bus stop  when you hover over it.

```js
    map.on('click', function(e) {
      var features = map.queryRenderedFeatures(e.point, {
        layers: ['bus-stops-milano-8ol8th'] // replace this with the name of the layer
      });
    
      if (!features.length) {
        return;
      }
    
      var feature = features[0];
      var popup = new mapboxgl.Popup({ offset: [0, -15] })
        .setLngLat(feature.geometry.coordinates)
        .setHTML('<h3>' + feature.properties.name + '</h3><p>' + feature.properties.operator + '/' + feature.properties.ref + '</p>')
        .setLngLat(feature.geometry.coordinates)
        .addTo(map);
    });
```

## 
![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532814998494_Build_a_map_with_Mapbox_GL_JS_at_SOTM2018.png)

## **Creating custom icons**
- Head to [Maki Icon Editor](https://www.mapbox.com/maki-icons/editor/)
- Customize the icons that you want by creating separate groups, picking colors, background etc.
- Download the iconset, and extract the svg icons from the zip
- In Mapbox Studio, add the custom icons (and replace the old ones) and update the layers that need these.
## **More tutorials and help**
- Check out the [Mapbox Studio Manual](https://www.mapbox.com/help/studio-manual/) for more guides
- Check out the [Mapbox GL JS examples](https://www.mapbox.com/mapbox-gl-js/examples/) to see how to make these maps interactive
## Follow up map ideas
- Display all bus routes on the map
![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532815163699_overpass_turbo.png)



- Select all the features you edited over time and show them on a map!
![](https://d2mxuefqeaa7sj.cloudfront.net/s_F042C157DC48532E7BD88EF4A3FC214820003375D03DB80E9873B62EE2667C9F_1532116623866_overpass_turbo.png)



- Instead of bus stop us a more complex feature. What about power stations?
- [Deploy your HTML page to Github pages](https://pages.github.com/) and tag us on Twitter with  @mapbox`
[](https://pages.github.com/)
 

