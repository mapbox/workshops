# Interactive visualizations for Remote sensing analysis

An introductory hands-on workshop on processing and analyzing satellite imagery for urban growth and vegetation cover in Hyderabad city.

Presentation link--> [FOSS4G_presentation.pdf](https://github.com/mapbox/hey/files/741285/FOSS4G_presentation.pdf)

## Workshop Description:

![screen shot 2017-01-31 at 2 46 38 pm](https://cloud.githubusercontent.com/assets/8401827/22458839/4d2ff6fc-e7c4-11e6-9810-410f42e878d2.png)


An introductory session on satellite imagery processing. In this hands-on workshop, we’ll introduce you to open satellite datasets, and teach you basics of image processing using open source tools. We will share real world examples on how to leverage open satellite imagery in digitize critical infrastructure, support disaster response efforts, and tell compelling stories. We'll introduce you to the world of design using Mapbox studio and help you to create a web application using Mapbox GL JS libraries. 

## Summary

- **Introduction**
 * Remote Sensing basics - Different types of satellites and image sources (Digital Globe, Landsat), resolution, bands, etc.,
- **Getting data**
 * [Landsat 7](https://earthexplorer.usgs.gov/) `(Search Criteria (select the area of interest) > Data sets > Landsat Archive > Pre Collection > L7 ETM+ SLC-on(1999-2003) > Additional Criteria > Cloud cover (Less than 10%) > Results)`
 * [Landsat 8](https://earthexplorer.usgs.gov/) `(Search Criteria (select the area of interest) > Data sets > Landsat Archive > Pre Collection > L8 OLI/TIRS & L8 OLI/TIRS Pre-WRS-2 > Additional Criteria > Cloud cover (Less than 10%) > Results)`

- **QGIS Intro**: 
 * [Introduction to QGIS](http://www.qgistutorials.com/en/)
 * Walk-through QGIS interface
 * Basic Raster analysis using QGIS

- **QGIS processing**:
 * Exploring different bands for identifying features of interest (use real-world examples)
 * Stacking bands of satellite images ([band combinations](https://blogs.esri.com/esri/arcgis/2013/07/24/band-combinations-for-landsat-8/))
 * Visualising different band combinations
 
- **Studio and mapbox tools**: 
 * Exhibiting examples - [Drying reservoirs](https://www.mapbox.com/blog/reservoirs-drying-landsat/) , [Forest fires](https://twitter.com/mapbox/status/727838137871818753) , [Mumbai landfill fire](https://www.mapbox.com/blog/mumbai-landfill-fire/)
 * Introduction to [Mapbox studio](https://www.mapbox.com/studio/) for design
 * Introduction for building a web app using [Mapbox gl js](https://www.mapbox.com/mapbox-gl-js/api/)
 
## Workshop Details

### Mapbox Satellite

![screen shot 2016-06-24 at 12 26 56](https://cloud.githubusercontent.com/assets/353700/16330478/1a2ec19a-3a07-11e6-967d-e5db9ffb91f5.png)<br>*[mapbox.com/satellite](https://www.mapbox.com/satellite/)*

### Basics of Satellite Image Processing

### QGIS processing intro:
We get RAW satellite imagery to download, which should be further processed to get it refined for our usage. To get a refined imagery we follow the following process: 

* **Radiometric correction of imagery**
   * Corrections for Sensor sensitivity
     * For optical sensors, due to use of lens a fringe area in the corners will be darker compared with the central region in the image. This called Vignetting. This can be calibrated using sensor output signal and irradiance. This information is supplied in the raw data.
   * **Sun angle and topography**
     * Bright spots often occur in the image due to diffusion of sun rays reflectance. These spots are called Sun spots. These can be corrected using known angle and fourier estimation of shading curve.
   * **Atmospheric correction**
     * Various atmospheric effects cause absorption and scattering of the solar radiation. Reflected or emitted radiation from an object and path radiance (atmospheric scattering) should be corrected for.
     * Pan Sharpening - Using a higher resolution greyscale image to optimize a color band image

* **Geometric Correction**
   * Establishing the relationship between the image coordinate system and the geographic coordinate system using calibration data of the sensor, measured data of position and attitude, ground control points, atmospheric condition etc.
   
### Using QGIS for performing basic image analysis

![image](https://cloud.githubusercontent.com/assets/13744156/16258090/be76c9e4-3879-11e6-8988-99b416271acc.png)<br>*QGIS Interface*


#### Opening a Raster File.

* In the Menu, **Layers > Add Layer > Add Raster Layer**.
* Select the raster layer file, i. e. `clip_PAN_LE71440482001062SGS00_B1.tif`.
* Click **OK**.

![raster](https://cloud.githubusercontent.com/assets/13744156/16258699/a0fa51ee-387c-11e6-8e28-de4216a9a9dd.png)


#### Processing the imagery for radiometric and geometric correction:

* In the Menu, **SCP > Bandset**.

![screen shot 2017-01-25 at 4 15 10 pm](https://cloud.githubusercontent.com/assets/8401827/22287606/7f392ca4-e319-11e6-8989-70853acd13ab.png)


* Select **Preprocessing > Landsat** in the pop-up.

![screen shot 2017-01-25 at 4 41 45 pm](https://cloud.githubusercontent.com/assets/8401827/22288531/32076ec4-e31d-11e6-82bb-10f8514f8318.png)


* Select the directory of Landsat 7 imagery `LE71440482001062SG00` in **Directory containing Landsat bands** option.
* Select the `MTL` file within the Landsat 7 directory in **Select MTL file (if not in Landsat directory)** option.
* Check-mark **Apply DOS1 atmospheric correction** and **Perform pansharpening (Landsat 7 & 8)**
* Remove Band 6 from options as the thermal band is not required for our processing.

![screen shot 2017-01-25 at 5 29 16 pm](https://cloud.githubusercontent.com/assets/8401827/22289880/d8964bf6-e323-11e6-830c-90325eb24dfd.png)


#### Clipping raster layer:
* In the Menu, **Layers > Add Layer > Add Vector Layer**.
* Select the vector layer file, i. e. `HYD.shp`.
* Click **OK**.

* In the Menu, **SCP > Bandset**.

![screen shot 2017-01-25 at 4 15 10 pm](https://cloud.githubusercontent.com/assets/8401827/22287606/7f392ca4-e319-11e6-8989-70853acd13ab.png)


* Select **Preprocessing > Clip multiple rasters** in the pop-up.
* Click refresh option on the right of **Raster list** to add all the bands to the list.
* Select the bands which we need to clip, in this case, clipped Band 1, Band 2, Band 3, Band 4, Band 5 & Band 7.
* Check-mark **Use shapefile for clipping** option and select the loaded `HYD.shp`.
* Click **RUN**


![screen shot 2017-01-25 at 5 46 07 pm](https://cloud.githubusercontent.com/assets/8401827/22290423/acb64eca-e326-11e6-9a60-a1960b7ef73b.png)


#### Stacking raster layers

* In the Menu, **SCP > Bandset**.

![screen shot 2017-01-25 at 4 15 10 pm](https://cloud.githubusercontent.com/assets/8401827/22287606/7f392ca4-e319-11e6-8989-70853acd13ab.png)


* Select the **Band Set** in the pop-up.
* Checkmark all the bands from Band list.
* Add them to Band set definition by clicking `+`.
* Arrange the bands in ascending order of band numbers (1-7) by clicking on arrows on the right.
* Select **Landsat 7 ETM+ [bands 1,2,3,4,5,7]** from the list in `Quick wavelength settings`.
* Click **RUN**

![screen shot 2017-01-25 at 4 23 57 pm](https://cloud.githubusercontent.com/assets/8401827/22287913/b6994bf6-e31a-11e6-81fe-55bdd4157fae.png)


#### Creating band combinations

 * False Color Composite/ Near-infrared 4-3-2
 * Click on the dropdown option of **RGB** where you can find pre-defined false color band combinations (4-3-2)
 
 ![screen shot 2017-01-25 at 4 31 21 pm](https://cloud.githubusercontent.com/assets/8401827/22288183/bf7cd02a-e31b-11e6-9d3d-9e60bc2e9ba6.png)
 
 * Right click on the stacked layer: `band_set.vrt`
 * Go to **Properties > Style**
 * In the **Rendering type**, choose **Multiband color**. 
 * Assign the following bands to:  
 
 **1** **Red band: Band 4**

 **2** **Green band: Band 3**
  
 **3** **Blue band: Band 2**

* Click **Apply > OK**. 
 
![screen shot 2017-01-25 at 4 33 52 pm](https://cloud.githubusercontent.com/assets/8401827/22288252/16393dfe-e31c-11e6-89e9-d84ce22b1f61.png)


#### Saving the final output:
* Right click on **band_set.vrt** and select `Save As...`
* Select **Rendered image** in pop-up
* Browse to the directory where you want to save the file in **Save as**
* Select **EPSG:4326, WGS 84** in CRS

![screen shot 2017-01-25 at 6 08 09 pm](https://cloud.githubusercontent.com/assets/8401827/22290873/4c9b0488-e329-11e6-8410-21d71908c7ca.png)


* Click **OK**

![screen shot 2017-01-25 at 6 08 18 pm](https://cloud.githubusercontent.com/assets/8401827/22290872/4c9989b4-e329-11e6-89da-02d6982b2247.png)

  
### Mapbox Studio


**Objective:** Understand customization of a map, `Styles`, `Tiles` and `Datasets`. Use the raster images we have generated in QGIS to overlay on `before` and `after`styles. Use Mapbox GL-JS to add interactivity to these maps with shareable links.


Sign up and create an account for Mapbox Studio - https://www.mapbox.com/studio/

Once you log in, go to `Styles`-> Click `New Style`
   
![screenshot_2017-01-25_11_27_37](https://cloud.githubusercontent.com/assets/8921295/22279578/81c94846-e2f1-11e6-8c51-f6d215609d53.jpg)


Select `Basic` to check the visual elements in this style to understand customization in Mapbox Studio

![image](https://cloud.githubusercontent.com/assets/8921295/22279629/d0632332-e2f1-11e6-9e85-3060871b5d00.png)



Select a `country_label` layer and change the text size and observe the live change on the map. We can also goto `Icon` tab and select a `maki` icon for each country label and remove the country_label `name`.

 
![studio_customization](https://cloud.githubusercontent.com/assets/8921295/22279794/e798fc1a-e2f2-11e6-8e5d-3425104c5af5.gif)



**Upload Raster images and add them to a style**

Go to `Tilesets` -> Click `New tileset`
   
![screenshot_2017-01-25_15_51_24](https://cloud.githubusercontent.com/assets/8921295/22286785/4e04c59c-e316-11e6-8a23-9932ac3b39c0.jpg)


Select the `.tif` file you have generated in QGIS to upload into Mapbox Studio

![image](https://cloud.githubusercontent.com/assets/8921295/22287275/2422e662-e318-11e6-82b5-11aad10d35d1.png)


Once it is uploaded, click on the tileset. If you have not generated these raster files, here are the examples you can use to add them into your styles [Before](https://www.mapbox.com/studio/tilesets/jothirnadh.4f3bdvkk/), [After](https://www.mapbox.com/studio/tilesets/jothirnadh.463ez364/).

Add these tilesets to a before map and an after map individually.

   
![image](https://cloud.githubusercontent.com/assets/8921295/22287371/a66f254a-e318-11e6-9100-5e2f50a6ed5e.png)


Select a new style in the dialog box and select `Satellite Streets` style and click `Create`. Mapbox Studio creates a style with `Mapbox Satellite` as background and overlays your raster tileset over it along with other label and road layers.

![image](https://cloud.githubusercontent.com/assets/8921295/22288398/bde16ea0-e31c-11e6-9ef8-3c774d5fd8b4.png)




Click `Create Layer`, Change the name of your style and then `Publish`. You have now created a map you can share with an URL.


![screenshot_2017-01-25_16_16_51](https://cloud.githubusercontent.com/assets/8921295/22288038/348db880-e31b-11e6-8d12-09d9a29793c5.jpg)


Click `Preview, develop & use` button in the dialog box that appears after you successfully publish.

Click the eye button to preview your style in the browser.


![screenshot_2017-01-25_16_24_090](https://cloud.githubusercontent.com/assets/8921295/22288237/0475f81e-e31c-11e6-979f-1314c24ba1a9.jpg)


Your map should look something similar to this.

![image](https://cloud.githubusercontent.com/assets/8921295/22288010/1bbb0330-e31b-11e6-9561-1f59e412936e.png)


Once we have both `before` map and `after` map, let us add the years on each style to add year information into each style. We can use Mapbox Studio Dataset editor for this.



### GL JS

* Sign up at https://github.com/
* Go to `Your profile` and click on `Repositories`.
![image](https://cloud.githubusercontent.com/assets/8921295/22290313/14135f8c-e326-11e6-8baf-b1be79d2548f.png)


Click `New` to create a repository. Give your repository a name.

![image](https://cloud.githubusercontent.com/assets/8921295/22290347/43b424ec-e326-11e6-81b9-d0a411ee2ccc.png)


Check `Initialize with a ReadMe file` to add a description file in your repository.

![image](https://cloud.githubusercontent.com/assets/8921295/22290386/7d630244-e326-11e6-9e14-ab7de9a2646e.png)

Now create a `gh-pages` branch that helps create a static map using Github.

![image](https://cloud.githubusercontent.com/assets/8921295/22290408/9d77a13e-e326-11e6-8e8d-053f5097411c.png)

You should see 2 branches in your repository and you should be in your new `gh-pages` repository.

![image](https://cloud.githubusercontent.com/assets/8921295/22290438/c222cdb0-e326-11e6-9ae5-efecc2a42e4f.png)
Click on `Create new file` to add our GL JS example code into a index.html file.

Example code: https://www.mapbox.com/mapbox-gl-js/example/mapbox-gl-compare/

![image](https://cloud.githubusercontent.com/assets/8921295/22290466/f1fa5d14-e326-11e6-9d5e-272de6e29dae.png)


Let us understand this code better.

### Basic HTML syntax
```
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        <h1>My First Heading</h1>
        <p>My first paragraph.</p>
    </body>
</html>
```
### The code that we use today for creating HTML application

[Swipe option from Mapbox GL JS](https://www.mapbox.com/mapbox-gl-js/example/mapbox-gl-compare/)

```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title></title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <!-- gl js javascript library -->
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.31.0/mapbox-gl.js'></script> 
    <!-- mapbox style sheet -->
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.31.0/mapbox-gl.css' rel='stylesheet' />
    <style>
        body { margin:0; padding:0; }
        /*map element*/
        #map { position:absolute; top:0; bottom:0; width:100%; }
    </style>
</head>
<body>

<style>
body {
    overflow: hidden;
}

body * {
   -webkit-touch-callout: none;
     -webkit-user-select: none;
        -moz-user-select: none;
         -ms-user-select: none;
             user-select: none;
}

/*map class*/
.map {
    position: absolute;
    top: 0;
    bottom: 0;
    width: 100%;
}
</style>
<script src='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.js'></script>
<link rel='stylesheet' href='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.css' type='text/css' />

<div id='before' class='map'></div>
<div id='after' class='map'></div>
<script>
mapboxgl.accessToken = 'pk.eyJ1Ijoiam90aGlybmFkaCIsImEiOiI0MTIzNmYwZmIzNWQ3MjFlNWE2YmE4YzU1YWQyNDdhOCJ9.afll1jVPlwiIoz0bJx51_g';
var beforeMap = new mapboxgl.Map({
    container: 'before',
    style: 'mapbox://styles/jothirnadh/ciybaolc300942rooovh8ujtz',
    center: [78.4882, 17.4008],
    zoom: 10,
    hash: true
});

var afterMap = new mapboxgl.Map({
    container: 'after',
    style: 'mapbox://styles/jothirnadh/ciybarfyq00992rod9hnc0mqw',
    center: [78.4882, 17.4008],
    zoom: 0,
    hash: true
});

var map = new mapboxgl.Compare(beforeMap, afterMap, {
    // Set this to enable comparing two maps by mouse movement:
    // mousemove: true
});   

</script>

</body>
</html>

```
#### Adding year labels to the web app:
```
afterMap.on('load', function () {
    afterMap.addSource("markers", {
        "type": "geojson",
        "data": {
            "type": "FeatureCollection",
            "features": [{
                "type": "Feature",
                "geometry": {
                    "type": "Point",
                    "coordinates": [78.7967,17.4745]
                },
                "properties": {
                    "title": "2016"
                }
            }]
        }
    });
    afterMap.addLayer({
        "id": "markers",
        "type": "symbol",
        "source": "markers",
        "layout": {
            "icon-image": "{marker-symbol}-15",
            "text-field": "{title}",
            "text-size": 50,
            "text-font": ["Open Sans Semibold", "Arial Unicode MS Bold"],
            "text-offset": [0, 0.6],
            "text-anchor": "top"
        }
    });
 });  
 beforeMap.on('load', function () {
    beforeMap.addSource("markers", {
        "type": "geojson",
        "data": {
            "type": "FeatureCollection",
            "features": [{
                "type": "Feature",
                "geometry": {
                    "type": "Point",
                    "coordinates": [78.1314,17.4553]
                },
                "properties": {
                    "title": "2001"
                }
            }]
        }
    });
    beforeMap.addLayer({
        "id": "markers",
        "type": "symbol",
        "source": "markers",
        "layout": {
            "icon-image": "{marker-symbol}-15",
            "text-field": "{title}",
            "text-size": 50,
            "text-font": ["Open Sans Semibold", "Arial Unicode MS Bold"],
            "text-offset": [0, 0.6],
            "text-anchor": "top"
        }
    });
 });
```
Commit your index.html code into your repository.

Go to settings in your repository to see the link to your map.
 
#### See also

* [Satellites in Global Development](http://landscape.satsummit.io/)
* [Electromagnetic Spectrum](http://www.ctahr.hawaii.edu/miuralab/projects/makaha/intro_RS.html)
* [Landsat 7 vs Landsat 8 comparison](http://landsat.gsfc.nasa.gov/?p=3186)
* [Spectral reflectance curve](http://www.geol-amu.org/notes/m1r-1-8.htm)
* [Band combination](http://landsat.usgs.gov/L8_band_combos.php)
* [Landsat information](http://www.geosage.com/highview/features_landsat8.html)
* [Semi Automatic classification plugin](http://fromgistors.blogspot.com/2015/07/major-update-semi-automatic-44.html)   

## Final Output 

The final output can be seen **[here](https://jothirnadh.github.io/test-swipe-map/#9.95/17.3968/78.4516)**
