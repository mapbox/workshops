# Satellite_workshop

The steps I followed to achieve the application are:

## Step 1 (Studio)
* Load the `.tiff` file of L8 and L7 into studio and create saperate styles (L8 and L7) for each.
* Make sure the loaded `.tiff` file is dragged below the other layers and publish them.

## Step -2 (Creating the basic app)
* Use the [Swipe between maps GL JS example](https://www.mapbox.com/mapbox-gl-js/example/mapbox-gl-compare/) as a source to build this app.
 * The above example is built using the [mapbox-gl-compare function](https://github.com/mapbox/mapbox-gl-compare)
* Replace the `accessToken` with your access tocken and give the appropriate style to before and after functions.
 * In this case 
 
after style = L8 style ID

before style = L7 style ID

## Step -3 (Defining a geojson)
* Create two different geojson files for `before` function and `after` function to represent the 1999 and 2015 in the application.

## Final Output

https://jothirnadh.github.io/Satellite_workshop/#
