# Mapbox Workshop FOSS4G 2018

> This workshop will cover working with Mapbox GL, Turf JS, and vector tiles. The goal of the activity is to show, in a hands-on way, how developers can use open source tools from the Mapbox GL ecosystem to create interactive, dynamic data visualizations from scratch.
## 

We guide through how to go from a open vector data to vector tiles and use it to create visualizations in a 5 step workshop.


## Outline
1. Find your [Vector Data](https://mangomap.com/gis-data)
  1. Get to know the formats (SHP, CSV, GeoJSON, OSM PBF)
  2. Great open data sets
    1. [OpenStreetMap](https://download.geofabrik.de/)
    2. [World Bank](https://datacatalog.worldbank.org/dataset/tanzania-roads)
2. Processing
  1. Join your tabular data with your vector data in QGIS (also possible with [tippecanoe join](https://github.com/mapbox/tippecanoe#tile-join))
3. Turn into Vector tiles
  1. using tippecanoe
  2. or by uploading to Mapbox.com
4. Styling
  1. Using Mapbox Studio to create a choropleth map
  2. What is Mapbox GL and how does it work
  3. What is the Mapbox style specification
5. Publish to the web
  1. Using Mapbox GL JS to filter the data you’ve added


----------


## 1. Vector Data

Before you create any visualization you will start with the source data that you have available.
Sometimes you have to create it yourself, other times you have a proprietary data set or in the best case you are able to use an open data portal to source your vector data.
For example the [World Bank data catalog](https://datacatalog.worldbank.org/) now provides spatial datasets as well. A good source for building any low scale map is [Natural Earth](https://www.naturalearthdata.com/downloads/50m-cultural-vectors/).

In this example we want to focus on comparing a data attribute across different sub units of a country (in the case of Tanzania “[regions](https://en.wikipedia.org/wiki/Regions_of_Tanzania)”).

**Picking a tabular data set**
On the [Basic Statistics Portal](http://opendata.go.tz/) of Tanzania we can find the number of deaths and their cause per region.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535333479190_Number_and_causes_of_death_occured_-_Datasets_-_Basic_Statistics_Tanzania.png)


👉🏽  Go to  http://opendata.go.tz/dataset/number-and-causes-of-death-occured-by-region and download the CSV for “Number and causes of death 5 and above years-2013”.

Save it as `deaths_2013` and open it in a spreadsheet editor.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535334355782_deaths_2013.png)


We will later be able to load that CSV file into QGIS but first we need to create a [CSVT file](https://anitagraser.com/2011/03/07/how-to-specify-data-types-of-csv-columns-for-use-in-qgis/) that describes which data types our columns are in (number or text).

The easiest way to complete that is to add a new header row and fill in the types for each column and then save it as CSV again.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535335391545_deaths_2013.png)


Now delete all the other rows except the first header row and save it with the same filename but with `.csvt` as suffix. If you look at your csvt file in a text editor make sure you have quotes wrapped around each field.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535335734051_Banners_and_Alerts_and_deaths_2013_csvt_and_how_to_create_a_csvt_file_-_Google_Search.png)


**Picking a spatial data set**
In order to visualize the number of deaths across regions  we have to find shapes for the appropriate 25 regions.

From the World Bank we can already find regional boundaries for Tanzania.

👉🏽  Go to  https://energydata.info/dataset/tanzania-region-district-boundary-2012 and download the zipped Shapefile for “Region bounday”.

As first step we are going to unzip the Shapefile and load the regions into QGIS to visualize them.
If we load the regions into QGIS we can explore them.

Drop the Shapefile into QGIS.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535334469266_QGIS_2_18_2_and_Tanzania_-_Region___District_Boundary__2012__-_Datasets_-_ENERGYDATA_INFO_and_Mapbox_Workshop_FOSS4G_2018__Dropbox_Paper.png)


Let’s assign a label to each boundary polygon by clicking on the layer and choosing the “Properties > Labels” panel.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535334738777_Layer_Properties_-_Regions___Labels_and_QGIS_2_18_2.png)



![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535334775349_QGIS_2_18_2.png)



>  We also get the total population to join http://www.nbs.go.tz/nbstz/index.php/english/statistics-by-subject/population-and-housing-census/844-tanzania-total-population-by-district-regions-2016.



## 2. Processing

We now have explored the source data (one tabular and one spatial) and in the next step [we are going to join each row for each region to the appropriate shape of that region in QGIS.](https://www.qgistutorials.com/en/docs/performing_table_joins.html)

**Add CSV file to QGIS**
From sourcing the vector data you should have both a CSV and a CSVT file with the same filename. Drop the CSV file into QGIS.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535336164131_QBJecjis48.gif)

![](/static/img/pixel.gif)


**Join the datasets by region**
Click on the Regions layer “Properties > Joins” and add a new vector join.
For both source and target choose the region as the join field.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535336308871_SrQ4oepxuu.gif)


If you open the attribute table of “Regions” now you should be able to see that we’ve joined all the deaths by cause columns to our original shape of the region.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535336455398_fi2d0mcDjQ.gif)


**Create a Choropleth in QGIS**

Click on “Properties > Style” for the region layer and choose “Graduated” as symbol and the column you want to visualize (the total deaths).

If you click “Classify” QGIS will automatically build a histogram and a color distribution.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535337164991_Layer_Properties_-_Regions___Style_and_QGIS_2_18_2.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535337266077_QGIS_2_18_2_and__Regions____Features_total__30__filtered__30__selected__0_and_Mapbox_Workshop_FOSS4G_2018__Dropbox_Paper_and_About_-_World_Bank_Group_-_Organizations_-_ENERGYDATA_INFO.png)



## 3. Vector Tiles

At this point we created a static choropleth map in QGIS.
In order to tell compelling stories our steps from here will show how to create the equivalent for the web to build a dynamic data visualization.

👨🏽‍🏫 Introduction into vector tiles

----------

If you are working with small data as we are dealing here you are able to directly convert this data into vector tiles using the Mapbox platform.

**Save file as GeoJSON**

You can save your existing Shapefile as GeoJSON and the joined attributes will be included.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535338418641_Save_vector_layer_as____and_QGIS_2_18_2_and__Regions____Features_total__30__filtered__30__selected__0_and_Upload_data_to_Mapbox___Mapbox.png)

## 

**Upload the GeoJSON to Mapbox**

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535338682424_sHRMyfAlXr.gif)


https://www.mapbox.com/help/uploads/
https://www.mapbox.com/help/uploads/#accepted-file-types-and-transfer-limits

After your GeoJSON has been processed successfully you will be able to inspect the tileset that has been created from the GeoJSON.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535338849662_zs5BE0UvNT.gif)



**Alternative: Turn the GeoJSON into vector tiles using tippecanoe**

----------

The open source tool tippecanoe can turn GeoJSON features into vector tiles.

👉🏽 [Install tippecanoe](https://github.com/mapbox/tippecanoe)

We can turn the GeoJSON we saved earlier directly into vector tiles.


    tippecanoe -o out.mbtiles -zg --drop-densest-as-needed $HOME/Documents/tanzania_deaths.geojson

An MBTiles file can be uploaded to Mapbox or you could also serve it on your own using a tileserver like https://github.com/klokantech/tileserver-gl.


## Styling

👨🏽‍🏫 Introduction to Mapbox Studio

https://www.mapbox.com/help/choropleth-studio-gl-pt-1/


![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1534825027145_Basic_Template___Mapbox_and_foss4g2018.png)


I am using http://colorbrewer2.org/ to create color schemas.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1534827266368_Basic_Template___Mapbox.png)


This is now a digital map you can use for story telling.
But we want to get one step further.


## Interactivity

In the next step we want to take our static map

- allow filtering the visualization by cause of death 
- add a popup to it to show more information about the deaths of each region
![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1534933904513_Causes_of_Deaths_in_Tanzania.png)


**Display a map**
As first step we create a HTML page that displays the map we made in Mapbox Studio.

👉🏽 Follow along https://www.mapbox.com/mapbox-gl-js/example/simple-map/

We create a new file `index.html` with a HTML skeleton.


    <!DOCTYPE html>
    <html>
    <head>
      <meta charset='utf-8' />
      <title>Causes of Deaths in Tanzania</title>
      <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
      <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.46.0/mapbox-gl.js'></script>
      <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.46.0/mapbox-gl.css' rel='stylesheet' />
      <link href="https://api.mapbox.com/mapbox-assembly/v0.23.0/assembly.min.css" rel="stylesheet">
      <script async defer src="https://api.mapbox.com/mapbox-assembly/v0.23.0/assembly.js"></script>
    </head>
    <body>
      <div class='flex-parent viewport-full relative clip'>
        <div id='map' class='flex-child flex-child--grow bg-darken10 viewport-twothirds viewport-full-ml'></div>
      </div>
    </body>
    </html>

On top of Mapbox GL we also add a little CSS framework to get started quickly. https://www.mapbox.com/assembly/

Now we need to initialize and add a map to the web page.


    <script>
    // your access token
    mapboxgl.accessToken = 'pk.eyXXX';
    var map = new mapboxgl.Map({
      container: 'map',
      // your style id
      style: 'mapbox://styles/yourusername/styleid',
      zoom: 6,
      // initialize the map to show Tanzania
      center: [35.170672, -8.459891],
      hash:true
    });
    </script>
![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535345677602_Causes_of_Deaths_in_Tanzania.png)


**Add a popup**


    <style>
    .mapboxgl-popup-content b {
      display: inline-block;
      width: 9em;
    }
    .mapboxgl-popup-content span {
      display: inline-block;
      min-width: 4em;
      text-align: right;
    }
    </style>


    function setupPopupHandler() {
      var popup = new mapboxgl.Popup({
          closeButton: false,
          closeOnClick: false
      });
    
      map.on('mousemove', function(e) {
        var features = map.queryRenderedFeatures(e.point, {layers: ['tanzania_deaths']});
        if(!features.length) {
          map.getCanvas().style.cursor = '';
          popup.remove();
        } else if (features.length > 0) {
          map.getCanvas().style.cursor = 'pointer';    
          var hoveredFeature = features[0];
          var props = hoveredFeature.properties;
          var popupHtml = "<b>Diabetes Mellitus:</b>"
            + "<span>" + props['deaths_2013_Diabetes Mellitus'] + "</span><br />"
            + "<b>Malaria severe:</b>"
            + "<span>" + props['deaths_2013_Malaria- Severe, Complicated'] + "</span>"
            + "<hr class='txt-hr my3'>"
            + "<b>Total Deaths:</b>"
            + "<span>" + props['deaths_2013_Total'] + "</span>";
          
          popup.setLngLat(e.lngLat)
               .setHTML(popupHtml)
               .addTo(map);
        }
      });
    }
    


    map.on('load', function () {
      // add zoom and rotation controls to the map.
      map.addControl(new mapboxgl.NavigationControl());
      setupPopupHandler();
    });

**Change attribute to interpolate across**

In Mapbox Studio we used the design editor to create our map. Under the hood
Mapbox Studio creates a JSON file describing how the map data should be rendered (the GL style document).

The code to describe the choropleth layer.


    {
      "id": "tanzania_deaths",
      "type": "fill",
      "source": "composite",
      "source-layer": "tanzadeaths-9dbsr2",
      "paint": {
        "fill-color": [
          "interpolate",
          ["linear"],
          ["get", "deaths_2013_Total"],
          301, "#fee8c8",
          1196, "#fdbb84",
          2090, "#e34a33"
        ]
      }
    }

Let’s decompose this. The `fill` type describes that we want to color a polygon and the `fill-color` paint property describes a [linear interpolation expression](https://www.mapbox.com/help/mapbox-gl-js-expressions/).
 
 With `["get", "deaths_2013_Total"]` we describe the field we want to use to interpolate the color across.
 And with `301, "#fee8c8", 1196, "#fdbb84", 2090, "#e34a33"` we define our color range. Meaning from the value `301` we start with the color `#fee8c8` and until 1196 we interpolate it towards `#fdbb84` after which until 2090 we interpolate towards `#e34a33`.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535346867236_Basic_Template___Mapbox.png)


 

If we want to switch out the attribute to interpolate across we have to change two arguments:

- the name of the field
- provide the data range for interpolation


    function colorRegions(interpolationField, stops) {
      if (stops.length < 3) throw new Error('Need to provide at least 3 stops to interpolate across');
      map.setPaintProperty('tanzania_deaths', 'fill-color', [
        "interpolate",
        ["linear"],
        ["get", interpolationField],
        stops[0], "#fee8c8",
        stops[1], "#fdbb84",
        stops[2], "#e34a33"
      ]);
    }



    var dataRanges = {
      'deaths_2013_Total': [301, 1196, 2090],
      'deaths_2013_Diabetes Mellitus': [1, 33, 65]
    };
    
    map.on('load', function () {
      // add zoom and rotation controls to the map.
      map.addControl(new mapboxgl.NavigationControl());
      setupPopupHandler();
      colorRegions('deaths_2013_Diabetes Mellitus', dataRanges['deaths_2013_Diabetes Mellitus'])
    });
![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535347505890_6dLNo21Dl9.gif)


**Add sidebar**


    <div class='flex-parent viewport-full relative clip'>
      <!-- insert sidebar here -->
      <div class="flex-child w-full w240-ml absolute static-ml left bottom">
        <div class="flex-parent flex-parent--column viewport-third h-full-ml hmax-full">
          <div class="flex-child flex-child--grow py12 px12 scroll-auto">
            <h2 class="txt-xl txt-bold mb6">Deaths in Tanzania</h2>
            <p class="txt-s"><strong class="txt-bold">Number and causes of death occured</strong> (2013) <br><strong class="txt-bold">Source:</strong> <a class="link link--blue-light" target="_blank" href="http://opendata.go.tz/dataset/number-and-causes-of-death-occured-by-region">http://opendata.go.tz/</a></p>
            <div id="filter-ui" class="mt12">
              <h4 class="txt-m txt-bold mb6">Cause of death</h4>
                <label class="radio-container">
                <input type="radio" name="radio-filter" value="deaths_2013_Total" checked="">
                <div class="radio mr6"> </div>
                <span>Total</span>
              </label><br>
              <label class="radio-container">
                <input type="radio" name="radio-filter" value="deaths_2013_Malaria- Severe, Complicated">
                <div class="radio mr6"> </div>
                <span>Malaria</span>
              </label><br>
              <label class="radio-container">
                <input type="radio" name="radio-filter" value="deaths_2013_Diabetes Mellitus">
                <div class="radio mr6"> </div>
                <span>Diabetes Mellitus</span>
              </label><br>
            </div>
          </div>
        </div>
      </div>
      <div id='map' class='flex-child flex-child--grow bg-darken10 viewport-twothirds viewport-full-ml'></div>
    </div>


    map.on('load', function () {
      // add zoom and rotation controls to the map.
      map.addControl(new mapboxgl.NavigationControl());
      setupPopupHandler();
      setupFilters();
    });


![](https://d2mxuefqeaa7sj.cloudfront.net/s_6552AB0028AE719237B17030D756B0987E7502EBDA68BD604E8071746D1363EF_1535347901595_aHM7hCF5Dz.gif)


