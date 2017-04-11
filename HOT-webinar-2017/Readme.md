# Webinar: Introduction to Mapbox Studio

**11th March, 2017** | **HOT Webinar**

Download the presentation: [Keynote (With videos)](), [PDF (Without videos)]()

## Getting started

We’ll use open source tools to extract OSM data, style it in Mapbox Studio, and then use an open platform to create an interactive demo. 

You’ll only need to sign up to a Mapbox account at [Mapbox.com](https://www.mapbox.com/studio/signup/).


## Final result

[Interactive Demo](https://jsfiddle.net/rasagy/bxg8rweq/2/embedded/result/)

## Finding a theme

Most often, you would have a dataset (in the form of a .csv, .geojson or other common geo-based data formats). For this webinar, we’ll start from scratch, and use data from OpenStreetMap.

Find a particular type of data (OSM tags) you want to use. We’ll use hospitals & clinics, details of which can be found on the [OSM wiki page](http://wiki.osm.org/) for [hospitals](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Dhospital).

These are defined as `amenity="hospital"` and `amenity="clinic"`.

## Extracting data from OSM

We’ll use [Overpass Turbo](https://overpass-turbo.eu/), that can allow us to zoom to a particular area on the map, and query for specific OSM features.

We can start by zooming in to Zimbabwe (or searching for Zimbabwe), and using the `Wizard` option to create queries:

- Start with `amenity="hospital"` ([Result](http://overpass-turbo.eu/s/ohs))
- We can restrict the search to a location (city, country etc.) — Try using `amenity="hospital" in "Zimbabwe"` ([Result](http://overpass-turbo.eu/s/oht ))
- We can include multiple tags using `&&` (and) / `||` (or) operators. Try using `(amenity="hospital" || amenity="clinic") in "Zimbabwe"` ([Result](http://overpass-turbo.eu/s/ohu))
- We’ll zoom to a [province](https://www.openstreetmap.org/relation/3336980) and style that data. Use (amenity="hospital" || amenity="clinic") in "Matabeleland North" ([Result](http://overpass-turbo.eu/s/ohq))
- We can export this data as a `geojson` so we can use this in Mapbox Studio

Tip: For complex queries, here’s a [quick introductory guide](https://github.com/mapbox/mapping/wiki/Overpass-Guide) and list of [commonly used queries](https://github.com/mapbox/mapping/wiki/Overpass:-Frequently-used-queries).


## Adding data to Mapbox Studio

Next, we’ll open [Mapbox Studio](https://www.mapbox.com/studio/). If you want to have an editable copy of the dataset, or want to create a dataset from scratch, you can use the Dataset Editor to create the dataset, and then export that as a tileset. In this case, we don’t want to edit the data, so we’ll directly create a tileset with this data by uploading it. 

Tip: You can read more about when to use Dataset Editor and when to directly use Tilesets in this [Mapbox Manual guide](https://www.mapbox.com/help/studio-manual-uploads/).

## Styling the data

With the tileset ready, we’ll add it to a new map style. 

- Click `Add to style` on the tileset page
- Give the style a name (like `Hospitals & Clinics in Zimbabwe`) and select `Basic` tempate
- In the `New layer` panel, select `Circle` and `Create layer`
- Play with the style properties, and with other layers

`Circle` works well for only nodes. In this case, we notice that polygons (like buildings) are shown as multiple circles, which isn’t what we want.

- Select your layer, and go to `Select data` tab
- Switch the layer type to `Symbol` (T)
- Click the `Style` tab to see more style properties you can edit now
- In the `Icon` tab, pick an icon (`hospital-15`)
- Explore other properties, such as `Allow icon overlap` in `Placement` tab

## Filtering data

We’ll create some distinction between the hospitals & clinics by making different layers for each.

- Select your layer, and go to `Select data` tab
- Click `Add filter` in the bottom, and select `amenity` field
- While keeping the condition as `is any of`, click on the `(empty)` field and set it as `hospital`
- Rename this layer as `hospitals`
- Duplicate the layer, and switch the filter value to `clinic`, and rename the layer accordingly
- In the `clinic` layer, select a smaller icon image (`hospital-11`), and reduce the size and opacity

## Publishing the map style

Once we’re happy with the style, we can `Publish` the style so it can be shared with others, or used for building more interactive maps.

- Click `Publish`, and review the changes
- Once published, click on the `eye` icon to preview your map style
- Notice the `Style URL` and `Access token`: these are used to link to your map style and specify your user credentials when you use this in any application


## Adding interactivity

Check out the [Mapbox GL JS examples](https://www.mapbox.com/mapbox-gl-js/examples/) to see how to make these maps interactive. We’ll start with two examples for this webinar.

- Open this [jsfiddle](https://jsfiddle.net/rasagy/sy0j1nqj/) and click on `Fork` to create a new copy
- Change the access token, style url, and layer names (in case you used something other than `hospitals` and `clinics` as your layer names)
- We have complete control over how we show the popup - Add a small text to the popup by editing the `setHTML()` line
- `Run` this to test this, and click `Embed` if you want to embed this on your website (For just a full screen view, just add `/embedded/result` to your url)

Here are two more ready to use code on jsfiddle: One for [showing/hiding the two layers](https://jsfiddle.net/rasagy/xx9cxbzj/), and one that [combines these two interactivity in one](https://jsfiddle.net/rasagy/typo415c/).

Feel free to explore more [Mapbox GL JS examples](https://www.mapbox.com/mapbox-gl-js/examples/)!

## Creating custom icons

- Head to [Maki Icon Editor](https://www.mapbox.com/maki-icons/editor/)
- Customize the icons that you want by creating separate groups, picking colors, background etc.
- Download the iconset, and extract the svg icons from the zip
- In Mapbox Studio, add the custom icons (and replace the old ones) and update the layers that need these.


## More tutorials and help
- Check out the [Mapbox Studio Manual](https://www.mapbox.com/help/studio-manual/) for more guides
- Check out the [Mapbox GL JS examples](https://www.mapbox.com/mapbox-gl-js/examples/) to see how to make these maps interactive
