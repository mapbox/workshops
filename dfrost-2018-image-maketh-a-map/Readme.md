## Image maketh a map! 
_Cartogram and Mapbox Studio workshop_ 

Resources: 
[resources.zip](https://github.com/mapbox/navigation-data/files/1820568/resources.zip)


## Getting Started: 

Here are a few resources you'll need before getting started:
- Mapbox account: Sign up for free at [Mapbox](https://www.mapbox.com/signup/)
- Quick intro to Mapbox Studio: While we’ll cover most topics in this workshop,[here’s a glimpse of how Mapbox Studio is structured.](https://www.mapbox.com/help/studio-manual/)

## How would it look?!


![image](https://user-images.githubusercontent.com/17887418/37551658-f07575ce-29c9-11e8-8f3c-796551114ad5.png)


## → Let’s head to 


## Cartogram: 

[Cartogram](www.mapbox.com/cartogram)

- Choose any image that will act as a reference to the style.
- Upload the image in the viewer to get started.
- Move the colour detectors around to choose the colours you want to customise the map with. 
- and viola, you have a beautiful custom map! 🙂 
- Add that style to Mapbox Studio to customise it further more! 

![cartogram](https://user-images.githubusercontent.com/17887418/37541196-a778511a-297f-11e8-84ab-179905496615.gif)


## To Mapbox Studio: 

- Download the common image.

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521134491486_image.png)

- Play around with cartogram and customise the map according to image.
- Click the `saved style` button to open your cartogram style on Mapbox Studio. 

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521220720683_Screen+Shot+2018-03-16+at+10.44.11+AM.png)

## Mapbox Studio: 

### Customize your style

#### Style background and water
  - Click on the background layer in the layer list
  - When the layer panel opens, change the `Color` field to #403347
  - Click on `value options` and select `set value by zoom` 
  - Select zoom `22` and set the colour field to #473433, so that when you zoom in, the background starts to change gradually from purple to brown, making rest of the elements on map pop up! 
  
![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521129732430_image.png)

  - Click on the water layer in the layer list
  - When the layer panel opens, change the `Color` field to #11142c, the water will look slightly darker than the background, making the layers easier to distinguish.
  - Click on the waterway layer in the layer list
  - When the layer panel opens, change the `Color` field to #11142c

_Group the elements to the same type for easier editing and understanding of hierarchy_

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521129961525_image.png)

#### Change fonts and options

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521130785009_image.png)
- Click on the groups for the Properties to show up.
- Click on colour tab and set the values accordingly: 
      - Country labels: #e679b7 - State labels: #f5ca84 - Marine: #8fbdea 
      - Place labels 1: #fcccab - Place labels 2: #f0f8b4 - Road labels: #efd4fc - Transit and waterway: #e1e2e3
      - POI labels: #deb5dc
  - In the list of layers, select the layers you want the similar colours for and change the colours accordingly.
  - Change the `text halo color` field to #702e2a
  - Click on the font tab and make the changes accordingly.
  - When the layer panel opens, make the changes to the font. `Press Start 2P`and `Minecraft` make the font look pixelated! That's kinda the whole theme :) 
  
![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521130732295_image.png)

- You can also make changes to all the layers at once by filtering the layers you want and changing the properties at once. 
    - Change `Arial Unicode MS Regular` to `Press Start 2P` 
    - Change `Arial Unicode MS Regular` to `Minecraft` 
  
![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521131985226_fonts.gif)

  - Change the colours and fonts of all layers according to the colour palette 
  
  
#### Style landuse

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521223208350_image.png)

- Select both the `landuse_park` and `landuse_overlay_national_park` layer
    - Tip: You can select multiple layers at once by holding down `command` (Mac) or `CTRL` (Windows) while clicking to select layers
  - When the layer panel opens, click on `value options` and add a zoom value. Between 0 and 22, change the `Fill color` field to #9c3066 and#fcc5ef  for national parks and #841c50 and #fcc5ef for parks, so that there is a gradual development of colour.
  - Change the `1px stroke` layer to #17FFDD
  
#### Style national boundaries

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521223300151_image.png)

- Select the layer `national` and set the colour #bdbdbd. Follow the same steps to change the colours for the borders or if you wish, you can retain the colours the cartogram has picked out for them. 

#### Style roads

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521133306487_image.png)

  - Select the layers `bridge`s, `roads`, `tunnels` 
  - Change the `color` to #ed3f51
  - Select the layers `bridge case`, `roads case` and `tunnel case`
  - Change the `color` to #841c50
  - Select the layers `bridge_major case`, `bridge_minor case`
  - Change the `color` to #908DE7
  
#### Style buildings

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521223553938_image.png)

  - Click on the building layer in the layer list.
  - Choose the option `set value by zoom` 
  - Change the `Color` field to #ad99ad and #bfabbf for the buildings to gradually change colours and not abruptly pick it up. 
  - Change the `1px stroke` field to #eb84b8
  - Set the opacity to 0.5 to make the buildings appear pastel and not too bright. 

#### Icons and patterns: 

- Create a custom set of icons using the maki icon editor. 
![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521221825351_icons.gif)
![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521221721359_image.png)

- Download the svgs and load it in Studio icon set. Set the icons for poi layer as `{maki}-11`

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521221961304_image.png)

- Create a custom pattern using heropatterns.com
- Download the pattern in svg format 
- Copy the layer for which you want to add the pattern 
- In the layer, click on pattern field and chose icon tab. Upload the svg you want use as a pattern and chose the svg. 
- Set the opacity to low value, so the pattern doesn’t appear too distinct and nicely blends into the background. 

![image](https://d2mxuefqeaa7sj.cloudfront.net/s_DB0EA5140564ADD762B2C0391467A0B1752AB12F822276C533B3F444410B7A28_1521222077659_patterns.gif)

## Share your map with us! 

Make your own custom map using [Cartogram](www.mapbox.com/cartogram) and [Studio](www.mapbox.com/studio) and share it with us using hashtag #maphackweekend and tag @Mapbox on Twitter!! :) 

## More tutorials and help
- Check out the [Mapbox Studio Manual](https://www.mapbox.com/help/studio-manual/) for more guides
- Check out the [Mapbox GL JS examples](https://www.mapbox.com/mapbox-gl-js/examples/) to see how to make these maps interactive

