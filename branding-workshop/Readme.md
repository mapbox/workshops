## Workshop: Designing custom maps for your brand

**4PM — 7PM | 3rd March, 2017 | Mapbox BLR**

Event page: [Mapbox](https://bit.ly/mapbox-branding-workshop), [Facebook](https://www.facebook.com/events/1369029886474104/)

-------

Download Presentation: [Keynote (~71MB, with videos)](https://github.com/mapbox/workshops/raw/gh-pages/branding-workshop/Workshop%20-%20Custom%20Maps%20for%20Brands.key), [PDF (~46MB, without videos)](https://github.com/mapbox/workshops/raw/gh-pages/branding-workshop/Workshop%20-%20Custom%20Maps%20for%20Brands.pdf)

[Watch Fb Live video here (~2.5hrs long)](https://www.facebook.com/Mapboxblr/videos/685615934950733/)

Check out the event photos on our [Flickr Page](https://www.flickr.com/photos/mapbox/sets/72157681213553285)

-------


## Getting started

Here are a few resources you'll need before getting started:

- **Mapbox account**: Sign up for free at [Mapbox.com](https://www.mapbox.com/studio/signup/).
- **Quick intro to Mapbox Studio**: While we’ll cover most topics in this workshop, here’s a [glimpse of how Mapbox Studio is structured](https://www.mapbox.com/help/studio-manual/).
- **Style guidelines**: Although not necessary, it is often helpful to start with some broad style guidelines when creating a custom map style. Here are the style guidelines for this guide:

![satellite-logo-guide](https://cloud.githubusercontent.com/assets/1117531/23547387/fadc25b0-0028-11e7-92d6-6061b355b34d.png)

**Colors:**
- #1E6799
- #1FABC8
- #F7DD0B
- #F58622
- #E45731
- #A5CE5D
- #D0E4AD
- #FFFFFF

## Create a new style

Create a new style from New Styles, and select **Basic** template.

## Customize your style

### Style background and water

<img width="1280" alt="screenshot 2017-03-01 16 38 56" src="https://cloud.githubusercontent.com/assets/1117531/23547371/ed5228fe-0028-11e7-8efa-e357277a38c5.png">

- Click on the **background** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#A5D05C'></span> `#A5CE5D`

<img width="1280" alt="screenshot 2017-03-01 16 39 07" src="https://cloud.githubusercontent.com/assets/1117531/23547372/ed52266a-0028-11e7-8ba4-51dbefcf884b.png">

- Click on the **water** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#256897'></span> `#1E6799`
- Click on the **waterway** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#256897'></span> `#1E6799`


### Style national parks

Then, change the color of both `landuse_park` and `landuse_overlay_national_park` using the Properties panel.

<img width="1280" alt="screenshot 2017-03-01 16 43 47" src="https://cloud.githubusercontent.com/assets/1117531/23547370/ed49b1e2-0028-11e7-8aa8-2334b7eb4d2b.png">

- Select both the `landuse_park` and `landuse_overlay_national_park` layer
    - *Tip: You can select multiple layers at once by holding down* `command` *(Mac) or* `CTRL` *(Windows) while clicking to select layers*
- When the layer panel opens, change the `Fill color` field to <span class='color-swatch' style='background-color:#A5D05C'></span> `#A5D05C`


### Change fonts and options

<img width="1280" alt="screenshot 2017-03-01 16 48 41" src="https://cloud.githubusercontent.com/assets/1117531/23547368/ed46f074-0028-11e7-9b5e-58089d450da0.png">

- Click **Properties** at the bottom of the layer list to open the Properties panel
- When the Properties list opens, click **Fonts**
- When the layer panel opens, make the following changes:
  - Change `Open Sans Semibold` to `Open Sans Bold`
  - Change `Open Sans Regular` to `Open Sans Bold`
  - Change `Open Sans Bold` to `Open Sans Extrabold`
- Select all the layers for labels except road labels
- Scroll down to find the `Text transform` property, and select the Uppercase <span class='icon transform-uppercase'></span> option


### Style labels

After you have changed the font and set some general options, it's time to change the colors of the labels to reflect the look of the Mapbox logo. First you will change the place labels and then the road labels.

#### Place labels

-  Select all country, place, and poi symbol layers: **country_label**, **place_label_city**, **place_label_other**, **poi_label**
- When the layer panel opens, change the `Color` field <span class='color-swatch' style='background-color:#fff;border:1px solid #094261'></span> `#FFFFFF`
- Change the `Halo color` field to <span class='color-swatch' style='background-color:#094261'></span> `#094261`
- Change the `Halo blur` field to `0px`


#### Road labels

<img width="1280" alt="screenshot 2017-03-01 17 42 01" src="https://cloud.githubusercontent.com/assets/1117531/23547366/ed275ffc-0028-11e7-9d8d-25e994c76217.png">

- Click **road_major_label** in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#094261'></span> `#094261`



### Style by zoom level

<img width="1280" alt="screenshot 2017-03-01 17 43 56" src="https://cloud.githubusercontent.com/assets/1117531/23547365/ed2673bc-0028-11e7-9733-5f41b558f193.png">

- Click on the **background** layer in the layer list
- When the layer panel opens, click the <span class='icon step-ramp'></span> icon next to the `Color` property
- Click the **Enable zoom function** button
- Add an additional stop by clicking **<span class='icon plus'></span>Add stop**
- Edit each stop (the text field on the left is the zoom level and the text field on the right is the color)
    - Edit the first stop so the zoom level is `4` and the color is green <span class='color-swatch' style='background-color:#A5D05C'></span> `#A5CE5D`
    - Edit the second stop so the zoom level is `10` and the color is light green <span class='color-swatch' style='background-color:#D0E4AD'></span> `#D0E4AD`
    - Edit the third stop so the zoom level is `18` and the color is yellow <span class='color-swatch' style='background-color:#F6DF46'></span> `#F7DD0B`
- Zoom in to see the background color change gradually as the zoom level increases


### Style buildings

<img width="1280" alt="screenshot 2017-03-01 17 50 36" src="https://cloud.githubusercontent.com/assets/1117531/23547363/ed22692a-0028-11e7-9bc1-b0f4d4ce25ee.png">

Next, you'll change the color of the buildings to reflect the style of the Mapbox logo.

- Click on the **building** layer in the layer list
- When the layer panel opens, change the `Color` field to <span class='color-swatch' style='background-color:#F68622'></span> `#F58622`
- Change the `Opacity` field to `0.6`
- Change the `1px stroke` field to <span class='color-swatch' style='background-color:#F68622'></span> `#F58622`

<img width="1280" alt="screenshot 2017-03-01 18 11 12" src="https://cloud.githubusercontent.com/assets/1117531/23547364/ed23cfe0-0028-11e7-99d8-0c1bf1f331a9.png">

- Click on the **building** layer in the layer list
- When the layer panel opens, click the <span class='icon step-ramp'></span> icon next to the `Opacity` property
- Click the **Enable zoom function** button
- Edit each stop (the text field on the left is the zoom level and the text field on the right is the opacity)
    - Edit the first stop so the zoom level is `15` and the opacity is `0`
    - Edit the second stop so the zoom level is `16` and the opacity is `0.6`
- Zoom in to see the buildings fade in between zoom level 15 and 16

### Icons & Patters
(To be demoed)
- https://www.mapbox.com/maki-icons/editor/
- http://www.heropatterns.com/
- https://www.toptal.com/designers/subtlepatterns/

### Filters
(To be demoed)
- https://www.mapbox.com/vector-tiles/mapbox-streets-v7/
- http://wiki.openstreetmap.org/wiki/Key:highway

### More
- https://www.mapbox.com/help/studio-manual/
