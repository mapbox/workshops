# Ottawa meetup, 4th August 2017
---

## OSMCha introduction

- https://osmcha.mapbox.com/
- Share your filter: https://osmcha.mapbox.com/filters?aoi=6ced03fb-3e8c-463d-a229-e7d7ee6de98e


## Mapbox Studio 101 

## Outline

1. Create a [Mapbox account](https://www.mapbox.com/studio/)
2. Interface tour
3. Create a new style
  * Style background and water
  * Change fonts
  * Style roads
  * Style buildings
4. Using Overpass to export data from OSM
5. Create a new tileset
6. Publishing your map.

**Quick intro to Mapbox Studio**: If you’re new to digital maps, here’ a [glimpse of how Mapbox Studio is structured](https://www.mapbox.com/help/studio-manual/#how-does-it-work).

## Create a new style

<img width="1280" alt="screenshot 2017-03-18 08 13 02" src="https://user-images.githubusercontent.com/371666/28003451-42e31030-6546-11e7-84e8-be5af22f481c.png">

Create a new style from New Styles, and select **Basic** template.

## Customize your style

### Style background and water

<img width="1280" alt="screenshot 2017-03-18 08 23 53" src="https://user-images.githubusercontent.com/371666/28003476-7de430f6-6546-11e7-8a51-4e0c906b6c54.png">


- Click on the **background** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#121132'>#121132</span>

<img width="1280" alt="screenshot 2017-03-18 08 24 52" src="https://user-images.githubusercontent.com/371666/28003488-a175248a-6546-11e7-8146-b7a5b37490fb.png">


- Click on the **water** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#000011'>#000011</span>
- Click on the **waterway** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#000011'>#000011</span>


### Change fonts and options


<img width="1280" alt="screenshot 2017-03-18 08 28 11" src="https://user-images.githubusercontent.com/371666/28003496-b6f6ea14-6546-11e7-8380-1976ce4abdd5.png">

- Click **Properties** at the bottom of the layer list to open the Properties panel
- When the Properties list opens, click **Colors**
- Filter the list of layers by selecting `T` on the top: this will show colors of all text labels
- Change the `text color` field to <span class='color-swatch' style='background-color:#17FFDD'>#17FFDD</span>
- Change the `text halo color` field to <span class='color-swatch' style='background-color:#000011'>#000011</span>

<img width="1280" alt="screenshot 2017-03-18 08 33 11" src="https://user-images.githubusercontent.com/371666/28003497-b6f9a38a-6546-11e7-9a80-f4b23c5b3dd8.png">

- In the Properties list, now click **Font stacks**
- When the layer panel opens, make the following changes:
  - Change `Open Sans Semibold` to `Magda Clean Mono Offc Pro Regular`
  - Change `Open Sans Regular` to `Magda Clean Offc Pro Regular`
  - Change `Open Sans Bold` to `Magda Clean Mono Offc Pro Bold`

### Style roads

<img width="1280" alt="screenshot 2017-03-18 08 50 31" src="https://user-images.githubusercontent.com/371666/28003528-f6468102-6546-11e7-9256-7f0f69e4861d.png">

- Select the layers `bridge_major`, `road_major`, `tunnel_major`
- Change the `color` to <span class='color-swatch' style='background-color:#6A66DB'>#6A66DB</span>

- Select the layers `bridge_minor`, `road_minor`, `tunnel_minor`
- Change the `color` to <span class='color-swatch' style='background-color:#2D2B54'>#2D2B54</span>

- Select the layers `bridge_major case`, `bridge_minor case`
- Change the `color` to <span class='color-swatch' style='background-color:#908DE7'>#908DE7</span>


### Style buildings

<img width="1280" alt="screenshot 2017-03-18 12 34 10" src="https://user-images.githubusercontent.com/371666/28003529-f649666a-6546-11e7-87d0-156e83ceddbe.png">

- Click on the **building** layer in the layer list
- Change the `Color` field to <span class='color-swatch' style='background-color:#2D2B54'>#2D2B54</span>
- Change the `1px stroke` field to <span class='color-swatch' style='background-color:#6A66DB'>#6A66DB</span>

## Finding a theme

![image](https://user-images.githubusercontent.com/371666/28003546-25848824-6547-11e7-97d8-cd94074f8a86.png)

Most often, you would have a dataset (in the form of a .csv, .geojson or other common geo-based data formats). For this session, we’ll start from scratch, and use data from OpenStreetMap.

Find a particular type of data (OSM tags) you want to use. We’ll use hospitals & clinics, details of which can be found on the [OSM wiki page](http://wiki.osm.org/) for [hospitals](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Dhospital).

These are defined as `amenity="hospital"` and `amenity="clinic"`.

## Extracting data from OSM

![image](https://user-images.githubusercontent.com/371666/28003565-3d9db30e-6547-11e7-8a3e-e039e2617a46.png)

We’ll use [Overpass Turbo](https://overpass-turbo.eu/), that can allow us to zoom to a particular area on the map, and query for specific OSM features.

We can start by zooming in to Ottawa (or searching for Ottawa), and using the `Wizard` option to create queries:

- Start with `amenity="hospital"` ([Result](http://overpass-turbo.eu/s/qMF))
- We can restrict the search to a location (city, country etc.) — Try using `amenity="hospital" in "Ottawa"` ([Result](http://overpass-turbo.eu/s/oht ))
- We can include multiple tags using `&&` (and) / `||` (or) operators. Try using `(amenity="hospital" || amenity="clinic") in "Ottawa"` ([Result](http://overpass-turbo.eu/s/qMH))
- We’ll zoom to a [province](https://www.openstreetmap.org/relation/4136816) and style that data. Use (amenity="hospital" || amenity="clinic") in "Ottawa" ([Result](http://overpass-turbo.eu/s/qMJ))
- We can export this data as a `geojson` so we can use this in Mapbox Studio

Tip: For complex queries, here’s a [quick introductory guide](https://github.com/mapbox/mapping/wiki/Overpass-Guide) and list of [commonly used queries](https://github.com/mapbox/mapping/wiki/Overpass:-Frequently-used-queries).


## Adding data to Mapbox Studio

![image](https://user-images.githubusercontent.com/371666/28003585-58cf1fb4-6547-11e7-81be-ce177aaa18cf.png)

Next, we’ll open [Mapbox Studio](https://www.mapbox.com/studio/). If you want to have an editable copy of the dataset, or want to create a dataset from scratch, you can use the Dataset Editor to create the dataset, and then export that as a tileset. In this case, we don’t want to edit the data, so we’ll directly create a tileset with this data by uploading it.

Tip: You can read more about when to use Dataset Editor and when to directly use Tilesets in this [Mapbox Manual guide](https://www.mapbox.com/help/studio-manual-uploads/).

## Styling the data

![image](https://user-images.githubusercontent.com/371666/28003589-65de6462-6547-11e7-9d07-5297e40e2ace.png)

With the tileset ready, we’ll add it to a new map style.

- Click `Add to style` on the tileset page
- Give the style a name (like `Hospitals & Clinics in Ottawa`) and select `Basic` tempate
- In the `New layer` panel, select `Circle` and `Create layer`
- Play with the style properties, and with other layers

`Circle` works well for only nodes. In this case, we notice that polygons (like buildings) are shown as multiple circles, which isn’t what we want.

- Select your layer, and go to `Select data` tab
- Switch the layer type to `Symbol` (T)
- Click the `Style` tab to see more style properties you can edit now
- In the `Icon` tab, pick an icon (`hospital-15`)
- Explore other properties, such as `Allow icon overlap` in `Placement` tab

## Filtering data

![image](https://user-images.githubusercontent.com/371666/28003599-7336030e-6547-11e7-8880-7e1e7ac1c0b8.png)
We’ll create some distinction between the hospitals & clinics by making different layers for each.

- Select your layer, and go to `Select data` tab
- Click `Add filter` in the bottom, and select `amenity` field
- While keeping the condition as `is any of`, click on the `(empty)` field and set it as `hospital`
- Rename this layer as `hospitals`
- Duplicate the layer, and switch the filter value to `clinic`, and rename the layer accordingly
- In the `clinic` layer, select a smaller icon image (`hospital-11`), and reduce the size and opacity

## Publishing the map style

![image](https://user-images.githubusercontent.com/371666/28003602-79322b20-6547-11e7-8060-c1df10c59339.png)

Once we’re happy with the style, we can `Publish` the style so it can be shared with others, or used for building more interactive maps.

- Click `Publish`, and review the changes
- Once published, click on the `eye` icon to preview your map style
- Notice the `Style URL` and `Access token`: these are used to link to your map style and specify your user credentials when you use this in any application

## Exploring further

Head to the [Mapbox Studio Style Editor guide](https://www.mapbox.com/help/studio-manual-styles/#style-editor) to know more about styling different types of layers, and try the [tutorials to add popups & more interactivity](https://www.mapbox.com/help/studio-manual-tutorials/).
