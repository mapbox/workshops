# Mapbox Bengaluru Satellite Workshop

* Data and QGIS installer
 * [Satellite workshop data](https://www.dropbox.com/sh/0rh6jdjvrsa29i7/AAB5Q8UORui1zowVgOovjILHa?dl=0) (`847 MB`)
 * `QGIS installer` (optional)
* [Satellite image of Bangalore - between 1999 and 2015](http://mapbox.github.io/workshops/satellite-workshop/)


![stellite_workshop](https://cloud.githubusercontent.com/assets/13744156/16257213/a3d8f512-3874-11e6-97cd-83344f1c39a3.png)
 **Workshop Description:**
 
 An introductory session on satellite imagery processing. In this hands-on workshop, we’ll introduce you to open satellite datasets, and teach you basics of image processing using open source tools. We will share real world examples on how to leverage open satellite imagery in digitize critical infrastructure, support disaster response efforts, and tell compelling stories.

---

## Summary

- **Introduction**
 * Mapbox Satellite
 * Satellite basics - Different types of satellites and image sources (Digital Globe, Landsat), resolution, bands, etc.,

- **QGIS Intro**: 
 * [Introduction to QGIS](http://www.qgistutorials.com/en/)
 * Walk-through QGIS interface
 * Basic Raster and Vector analysis using QGIS

- **QGIS processing**:
 * Exploring different bands for identifying features of interest (use real world examples)
 * Stacking bands of satellite images ([band combinations](https://blogs.esri.com/esri/arcgis/2013/07/24/band-combinations-for-landsat-8/))
 * Visualising different band combinations
 
- **Studio and mapbox tools**: 
 * Exhibiting examples - [Drying reservoirs](https://www.mapbox.com/blog/reservoirs-drying-landsat/) , [Forest fires](https://twitter.com/mapbox/status/727838137871818753) , [Mumbai landfill fire](https://www.mapbox.com/blog/mumbai-landfill-fire/)

## Workshop Details

### Mapbox Satellite

![screen shot 2016-06-24 at 12 26 56](https://cloud.githubusercontent.com/assets/353700/16330478/1a2ec19a-3a07-11e6-967d-e5db9ffb91f5.png)<br>*[mapbox.com/satellite](https://www.mapbox.com/satellite/)*

### Basics of Satellite Image Processing

**What is light?**

![shutterstock_154169990](https://cloud.githubusercontent.com/assets/353700/16329021/531b612a-39fd-11e6-98e0-11eef964e46f.jpg)<br>*[Relax. Your wearable tech isn't killing you slowly](http://www.komando.com/happening-now/300938/relax-your-wearable-tech-isnt-killing-you-slowly/all)*

**How to choose a satellite provider**

* How much image detail do I need (spatial resolution)?

![resolution](https://cloud.githubusercontent.com/assets/353700/16329721/d5214532-3a01-11e6-8946-2c2df4f4239f.gif)

![screen shot 2016-06-24 at 11 42 14](https://cloud.githubusercontent.com/assets/353700/16329506/c8a7e0f0-3a00-11e6-8e9f-6f74a1280455.png)<br>*Cost vs Resolution*

* Revisit frequency to study a feature of interest (temporal resolution)?

![revisit](https://cloud.githubusercontent.com/assets/353700/16329774/31765188-3a02-11e6-91a8-2309b61c5142.gif)

![screen shot 2016-06-24 at 11 4157](https://cloud.githubusercontent.com/assets/353700/16329505/c8a79096-3a00-11e6-863a-6361603584d7.png )<br>*Cost vs Revisit*

* Features to be detected, based on their spectral signatures (spectral resolution)?
 
![spectral](https://cloud.githubusercontent.com/assets/353700/16329846/b76052b2-3a02-11e6-8b56-94ff9efcac28.gif)


### Using QGIS for performing basic image analysis

![image](https://cloud.githubusercontent.com/assets/13744156/16258090/be76c9e4-3879-11e6-8988-99b416271acc.png)<br>*QGIS Interface*


#### Opening a Raster File.

* In the Menu, **Layers > Add Layer > Add Raster Layer**.
* Select the raster layer file, i. e. `clip_PAN_LE71440511999313SGS00_B1.tif`.
* Click **OK**.

![raster](https://cloud.githubusercontent.com/assets/13744156/16258699/a0fa51ee-387c-11e6-8e28-de4216a9a9dd.png)

#### Stacking raster layers

* In the Menu, **Raster > Miscellaneous > Merge**.

![](https://cloud.githubusercontent.com/assets/13744156/16258903/984dcae8-387d-11e6-947c-f44b9a62d70a.png)

* Select the **Input** layers.
* Create an **Output** layer file.
* Check the **No data value** option.
* Check the **Layer Stack** option.
* Click **OK**.


![merge2](https://cloud.githubusercontent.com/assets/13744156/16259032/461ef520-387e-11e6-90cc-e312f8536833.png)

#### Creating band combinations

 * False Colour Composite/ Near infrared 4-3-2
 * Right click on the stacked layer: `landsatxxxxBandstack.tif`
 * Go to **Properties > Style**
 * In the **Rendering type**, choose **Multiband color**. 
 * Assign the following bands to:  
 
 **1** **Red band: Band 4**

 **2** **Green band: Band 3**
  
 **3** **Blue band: Band 2**
  
* Click **Load**. 
* Click **Apply > OK**. 
 
![screen shot 2016-06-24 at 1 06 41 pm](https://cloud.githubusercontent.com/assets/13744156/16331236/9037caf8-3a0c-11e6-826a-1ac33349619d.png)



#### Computing ([NDVI](https://en.wikipedia.org/wiki/Normalized_Difference_Vegetation_Index)) with raster calculator.


* In the Menu, choose **Raster > Raster Calculator**.

![screen shot 2016-06-22 at 3 16 56 pm](https://cloud.githubusercontent.com/assets/13744156/16262246/6637d8fa-388c-11e6-8df7-0899d5123b2c.png)

* In the raster calculator, enter the following expression(vegetation index): **(BAND 4 - BAND 3)/(BAND 4 + BAND 3)**

![screen shot 2016-06-22 at 2 40 36 pm](https://cloud.githubusercontent.com/assets/13744156/16261000/64b7e97a-3887-11e6-839b-a50fb383d142.png)

* Assigning psuedocolor to the NDVI image (for better visualization):

  * Right click on the NDVI Layer **> Properties > Style**.
 
  * In the **Style** dialog, apply the folowing changes:
 
  * Assign: `Greens`
 
  * Rendertype: **Singleband Psuedocolor**
 
  * Mode: **Equal Interval**
 
  * Classes: **10**
 
  * Click **Classify**.
 
  * Click **Min/max**

  * CLick: **Load**
 
  * Click **Apply > OK**.
 
![screen shot 2016-06-24 at 1 02 59 pm](https://cloud.githubusercontent.com/assets/13744156/16331201/36a4f2b8-3a0c-11e6-9370-917a49d71129.png)



#### See also

* [Principles of Remote Sensing](http://www.itc.nl/library/papers_2009/general/PrinciplesRemoteSensing.pdf)
* [Satellites in Global Development](http://landscape.satsummit.io/)
* [Electromagnetic Spectrum](http://www.ctahr.hawaii.edu/miuralab/projects/makaha/intro_RS.html)
* [Landsat 7 vs Landsat 8 comparison](http://landsat.gsfc.nasa.gov/?p=3186)
* [Spectral reflectance curve](http://www.geol-amu.org/notes/m1r-1-8.htm)
* [Band combination](http://landsat.usgs.gov/L8_band_combos.php)
* [Landsat information](http://www.geosage.com/highview/features_landsat8.html)
* [Semi Automatic classification plugin](http://fromgistors.blogspot.com/2015/07/major-update-semi-automatic-44.html)

--

The steps involved in making the application are:

## Step 1 ([Mapbox Studio](https://www.mapbox.com/studio))

* Go to [Mapbox Studio](https://www.mapbox.com/studio).
* Load the `.tiff` file of L8 and L7 into studio and create saperate styles (L8 and L7) for each.
* Make sure the loaded `.tiff` file is dragged below the other layers and publish them.

## Step 2 (Creating the basic app)

* Use the [Swipe between maps GL JS example](https://www.mapbox.com/mapbox-gl-js/example/mapbox-gl-compare/) as a source to build this app.
 * The above example is built using the [mapbox-gl-compare function](https://github.com/mapbox/mapbox-gl-compare)
* Replace the `accessToken` with your access token and give the appropriate style to before and after functions.
 * In this case 
 
after style = L8 style ID

before style = L7 style ID

## Step 3 (Defining a geojson)

* Create two different geojson files for `before` function and `after` function to represent the **1999** and **2015** in the application.

## Final Output 

The final output can be seen **[here](http://mapbox.github.io/workshops/satellite-workshop/)**

