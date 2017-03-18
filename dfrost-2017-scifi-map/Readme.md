# Futuristic Map Design workshop at Dfrost 2017

Held at **National Institute of Design, Bangalore** | On **18th March, 2017**

Download the [workshop resources](https://github.com/mapbox/workshops/raw/gh-pages/dfrost-2017-scifi-map/Workshop%20Resources.zip)

## Getting started

Here are a few resources you'll need before getting started:

- **Mapbox account**: Sign up for free at [Mapbox.com](https://www.mapbox.com/studio/signup/).
- **Quick intro to Mapbox Studio**: While we’ll cover most topics in this workshop, here’s a [glimpse of how Mapbox Studio is structured](https://www.mapbox.com/help/studio-manual/).
- **Style guidelines**: Although not necessary, it is often helpful to start with some broad style guidelines, or a set of colors when creating a custom map style. 

**Colors for today’s workshop:**

- <span class='color-swatch' style='background-color:#000011'>#000011</span>
- <span class='color-swatch' style='background-color:#121132'>#121132</span>
- <span class='color-swatch' style='background-color:#1E221D'>#1E221D</span>
- <span class='color-swatch' style='background-color:#17FFDD'>#17FFDD</span>
- <span class='color-swatch' style='background-color:#2D2B54'>#2D2B54</span>
- <span class='color-swatch' style='background-color:#6A66DB'>#6A66DB</span>
- <span class='color-swatch' style='background-color:#908DE7'>#908DE7</span>


## Create a new style

Create a new style from New Styles, and select **Basic** template.

## Customize your style

### Style background and water

<img width="1280" src="https://cloud.githubusercontent.com/assets/1117531/23547371/ed5228fe-0028-11e7-8efa-e357277a38c5.png">

- Click on the **background** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#121132'>#121132</span>

<img width="1280" src="https://cloud.githubusercontent.com/assets/1117531/23547372/ed52266a-0028-11e7-8ba4-51dbefcf884b.png">

- Click on the **water** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#000011'>#000011</span>
- Click on the **waterway** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#000011'>#000011</span>


### Change fonts and options

<img width="1280" src="https://cloud.githubusercontent.com/assets/1117531/23547368/ed46f074-0028-11e7-9b5e-58089d450da0.png">

- Click **Properties** at the bottom of the layer list to open the Properties panel
- When the Properties list opens, click **Colors**
- Filter the list of layers by selecting `T` on the top: this will show colors of all text labels
- Change the `text color` field to <span class='color-swatch' style='background-color:#17FFDD'>#17FFDD</span>
- Change the `text halo color` field to <span class='color-swatch' style='background-color:#000011'>#000011</span>

- In the Properties list, now click **Font stacks**
- When the layer panel opens, make the following changes:
  - Change `Open Sans Semibold` to `Magda Clean Mono Offc Pro Regular`
  - Change `Open Sans Regular` to `Magda Clean Offc Pro Regular`
  - Change `Open Sans Bold` to `Magda Clean Mono Offc Pro Bold`

- Select the layer for `country_label`
- Scroll down to find the `Text transform` property, and select the Uppercase <span class='icon transform-uppercase'></span> option


### Style national parks

<img width="1280" src="https://cloud.githubusercontent.com/assets/1117531/23547370/ed49b1e2-0028-11e7-8aa8-2334b7eb4d2b.png">

- Select both the `landuse_park` and `landuse_overlay_national_park` layer
    - *Tip: You can select multiple layers at once by holding down* `command` *(Mac) or* `CTRL` *(Windows) while clicking to select layers*
- When the layer panel opens, change the `Fill color` field to <span class='color-swatch' style='background-color:#1E221D'>#1E221D</span>
- Change the `1px stroke` layer to <span class='color-swatch' style='background-color:#17FFDD'>#17FFDD</span>

### Style national boundaries

- Select the layer `admin_country`
- Click on the `steps` button next to the `color` field, and then select the `Values` tab
- Scroll down to pick the same neon teal shade: <span class='color-swatch' style='background-color:#17FFDD'>#17FFDD</span>


### Style roads

- Select the layers `bridge_major`, `road_major`, `tunnel_major`
- Change the `color` to <span class='color-swatch' style='background-color:#6A66DB'>#6A66DB</span>

- Select the layers `bridge_minor`, `road_minor`, `tunnel_minor`
- Change the `color` to <span class='color-swatch' style='background-color:#2D2B54'>#2D2B54</span>

- Select the layers `bridge_major case`, `bridge_minor case`
- Change the `color` to <span class='color-swatch' style='background-color:#908DE7'>#908DE7</span>


### Style buildings

<img width="1280" src="https://cloud.githubusercontent.com/assets/1117531/23547363/ed22692a-0028-11e7-9bc1-b0f4d4ce25ee.png">

- Click on the **building** layer in the layer list
- Change the `Color` field to <span class='color-swatch' style='background-color:#2D2B54'>#2D2B54</span>
- Change the `1px stroke` field to <span class='color-swatch' style='background-color:#6A66DB'>#6A66DB</span>


### Icons & Patterns
(To be demoed)

- Create a custom maki icon set using the [Maki Editor](https://www.mapbox.com/maki-icons/editor/)
- Create a few custom patterns using [Hero Patterns](http://www.heropatterns.com/)
- Upload all of them to Mapbox Studio

### Filters
(To be demoed)

- Update the filters in poi_label by going to `Select Data` and changing the `localrank` to `less than 25` and the `scalerank` to `less than 5`
- To read more about what these are, and how the Mapbox data is structured, refer to the [Mapbox Streets Vector Tile reference](https://www.mapbox.com/vector-tiles/mapbox-streets-v7/) and the [OSM wiki](http://wiki.openstreetmap.org/wiki/Key:highway)

### More tutorials and help
- Check out the [Mapbox Studio Manual](https://www.mapbox.com/help/studio-manual/) for more guides
- Check out the [Mapbox GL JS examples](https://www.mapbox.com/mapbox-gl-js/examples/) to see how to make these maps interactive
