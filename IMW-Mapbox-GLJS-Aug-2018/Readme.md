# Mapbox GL JS - Coding is cool! (90 min workshop)

**You’ll need:**

- Mapbox account ([sign up](https://www.mapbox.com/signup/))
- [Github account](https://github.com/join)
- [Sublime Text editor](https://www.sublimetext.com/)
- Datasets (there are practice ones linked in the tutorials below and in the Mapbox folder on your USB drive)

**Reference links:**
[https://www.mapbox.com/mapbox-gl-js/api/](https://www.mapbox.com/mapbox-gl-js/api/)
[https://www.mapbox.com/mapbox-gl-js/examples](https://www.mapbox.com/mapbox-gl-js/examples) 

## Part 1: Orientation

**→ First - create a free Mapbox account at [https://www.mapbox.com/signup/](https://www.mapbox.com/signup/)
If you have a Mapbox account, log in, if not sign up for Mapbox. It’s totally free to sign up. You need a Mapbox account to get your Mapbox Access token.
**→ Quick intro to Mapbox GL JS (how and why to use this)**

- A Mapbox Studio style share URL only have basic interactivity, how can you add more? 
- Maps made with Mapbox GL JS for more design control and interactivity: [https://native-land.ca/](https://native-land.ca/) or [https://www.mapbox.com/amnesty/](https://www.mapbox.com/amnesty/) or [https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html](https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html) 


## Part 2: Intro to web development

**This is a very beginner intro by a non-developer - there’s a lot more to learn about developing more complex sites, but we’re focusing just on a simple web map. For more complex projects, you’ll want to learn more about version control and using Github properly, with pull requests etc.**

**→ Orientation Sublime Text**

- Open Sublime Text text editor software
- Use javascript to initialize a simple map: copy [this sample code](https://www.mapbox.com/mapbox-gl-js/example/simple-map/) into a new Sublime Text file and edit it to put in your Mapbox [access token](https://www.mapbox.com/help/define-access-token/).
- Save as `index.html`
- Right-click, select ‘view in browser’ (Chrome recommended)

*Wow! But this is just serving the map directly from your computer, it isn’t a webpage yet… to do that we need to use:*
**→ Orientation to Github Pages** 

- Set up a Github [repository](https://help.github.com/articles/create-a-repo/) 
- Upload your new index.html file to your Github repo
- [Enable Github Pages](https://pages.github.com/) (in repo Settings)
![](https://lh3.googleusercontent.com/WoPYoSwjki2aNcJaxPIt5Z6l7dtLEMYaJds-K-b-Ws9QpC27vEzmoOZbVYuex29WPFmIh5CopQJjKLHK6h4gts23fyxwtAMWqk4fztJ0fZGG7RBPL5fDGCHuoc5hK6qOBDUVYAnh)

- Then wait a minute, then go to your Github page address (https://[YOUR GITHUB NAME].github.io/[YOUR REPO NAME]/)  … you might need to wait another minute if it doesn’t work…

*Voila! Now you have a live website with a mapbox map! That wasn’t so bad ;)*

![](https://lh4.googleusercontent.com/defyWoLHlu9qtanped6JeppqjKOy6u0yMs4jLKwjrnwwvdlr_lMw0ItIyJ3HLuTdxX5bKbpBl8XlaJbVaXisofMwk3-TJvwSytZLauspFjI7mFRiuNnZ9vRfnL2ALU6u87NNV1s1)


**→ Now flex those new web development muscles**
*Let’s try making a change in the code for the web page*

- Currently, the tab for your webpage in your browser says ‘Display a map’ - let’s give it a better title - can you see where in the code to change that?
- Change it in Sublime Text, save, and right-click to see your change. If you like it, you can make the same change in the file you uploaded to Github (either copy-paste the whole thing and replace the whole thing, or just replace that one part). Commit your change, give it a minute, and check your webpage.

*Let’s try a change in the code that changes the map*

- Right now, the map opens looking at New Jersey, let’s change the location. Can you find where in the code is telling the map where to center the view?
- Try changing the center location by picking a new coordinate using [http://geojson.io/](http://geojson.io/#map=2/20.0/0.0) (or looking at the bottom of the right-hand panel in the Mapbox Studio style editor)
- Again, change it in Sublime Text, save, right-click to see your changes, and if you’re happy with them make the same change to your file in Github.
- Bonus: try changing the zoom level too!

*Let’s try a change that adds a new element to the map*

- We want to add navigation controls (zoom in, zoom out, and north arrow)
- Check out this code: [https://www.mapbox.com/mapbox-gl-js/example/navigation/](https://www.mapbox.com/mapbox-gl-js/example/navigation/)
- What is the part that’s missing for your current code? Copy and paste it into your code after your `var = map` element but before the </script>
- Change it in Sublime Text, save, right-click to see your changes, and if you’re happy with them make the same change to your file in Github.

*Let’s try switching to a custom style*

- Choose a style you have in your Mapbox Studio account, or make a quick one using Mapbox’s fun little [Cartogram](https://www.mapbox.com/cartogram/#13.01/40.7251/-74.0051) tool and a photo or logo of your choice (make the style and click `Saved style!` at the top to add it to your Studio account.
- Find your Style ID (info: [https://www.mapbox.com/help/define-style-id/](https://www.mapbox.com/help/define-style-id/))
- Switch it in the code in Sublime Text, save, right-click to see your changes, and if you like it make the same change in your Github file.

*Let’s look ‘under the hood’ of a more complex map*

- Go to [https://www.mapbox.com/amnesty/](https://www.mapbox.com/amnesty/) 
- In Chrome, click `View` then `Developer` then `Developer Tools` and look at the `Elements` tab. As you hover over lines in the Elements tab, you’ll see things be highlighted in the webpage.
- Look for the <script> tag
![](https://lh4.googleusercontent.com/3E8o5hec1HW4UnaEnokpcde5uD_pS7Dwtv38GQKatiuFEkDhZAu_XsfLjEzIyP5chcjZER-aL8T8BVmb8gP3xCaixM05FJYKmI41aQxnf8Xg1SF4aqcqRAQJU8Kfc9oOUNeBBsx6)

- See anything familiar? 
- Check out the full index.html code (a bit easier to read than in the Developer Console) by clicking `View` > `Developer` > `View source`. This is a more complex webpage, so there’s more CSS and Javascript going on, but you should be able to spot elements similar to what you just made. 
## Part 3: Hands-on project

You have two options:
**Option 1: Add interactivity to your existing choropleth**
If you attended the [Mapbox Studio session](https://docs.google.com/document/d/17Zvpg2UHvqX3doGI-dsA0r3fIZOGr7FAnXwZoyGizz8/edit#heading=h.tpkdn9bvd28w) and made a choropleth, you can add interactivity to your choropleth using the steps outlines in this tutorial: [https://www.mapbox.com/help/choropleth-studio-gl-pt-2/](https://www.mapbox.com/help/choropleth-studio-gl-pt-2/) 
**Tips**:

- I like to start with the code for a simple map (like what we made above) and add in new elements (just make sure you aren’t duplicating things that are already in your code).
- If in doubt on where something goes in the code, check out the [finished map](https://www.mapbox.com/help/demos/choropleth-studio-gl/demo-five.html) from the tutorial and click `View` > `Developer` > `View source` to see the code. You can also check out my final code for the Canada-ized version here: [https://github.com/marenab/IMW-2018/blob/master/index.html](https://github.com/marenab/IMW-2018/blob/master/index.html) 
- You’ll need to change the Style ID in your code to use the choropleth style you made yesterday: [https://www.mapbox.com/mapbox-gl-js/example/custom-style-id/](https://www.mapbox.com/mapbox-gl-js/example/custom-style-id/) (if you use your own, please see the **Important** section below) or you can try this using my existing choropleth style because I’ve made it a Public Style (and the tilesets it uses Public Tilesets):

mapbox://styles/marenab/cjl2oczit56x42rlxm5adlopg 
(You should be able to use this style ID with your own Mapbox access token - if it doesn’t seem to be working, you can contact [marena.brinkhurst@mapbox.com](mailto:marena.brinkhurst@mapbox.com) )

- If you are using your own Style, make sure your Style is [Published](https://www.mapbox.com/studio-manual/overview/publish-your-style/), or else it won’t work.

**Important**! 
The tutorial builds on the [Part 1 tutorial](https://www.mapbox.com/help/choropleth-studio-gl-pt-1/) using US data - if you made your choropleth map using the Canada data we used in the session, you’ll need to watch out for things that might be a bit different. Here are some critical ones:
**Legend colors**
If you are using your *own* choropleth style: make sure you know your `stops` that you used to color your choropleth because that is what the javascript will be referring to when it creates your legend. In your Studio style, your `can-pop` layer should look like:

![](https://lh6.googleusercontent.com/SCVFN7GzaJhCjGAqvw-SW88PC2qEqkziWlnHfM_uFxA4tOh20e6Z8g1MYSrJa70AsybAahH_HYV3XNVhiHF3sgrRqqXelEF9Za0DMhXD3h5c1BoOcyrr2zsVulbHWF_5OyzORcSv)


Then when you [create an array of intervals and colors](https://www.mapbox.com/help/choropleth-studio-gl-pt-2/#create-arrays-of-intervals-and-colors) following the tutorial, you’ll need to input your style’s particular stop values and color codes. For my style, instead of
var layers *=* ['0-10', '10-20', '20-50', '50-100', '100-200', '200-500', '500-1000', '1000+'];
var colors *=* ['#FFEDA0', '#FED976', '#FEB24C', '#FD8D3C', '#FC4E2A', '#E31A1C', '#BD0026', '#800026'];
For intervals and colors, I should use:
var layers *=* ['1730-10000', '10000-50000', '50000-100000', '100000-150000', '150000+'];
var colors *=* ['#FFEDA0', '#cfecd9', '#a0dab3', '#40b7c4', '#3195a0', '#253393'];
**Layer name for map.on(‘mousemove’)**
You’ll also need to modify the step for “adding the info window.” You have to use the correct name of the layer and data fields that you used in your Style (in Mapbox Studio). For the choropleth session, we used `canada-pop` instead of `statedata` as our layer, so instead of
map.on('mousemove', function(e) {
  var states *=* map.queryRenderedFeatures(e.point, {
    layers: ['statedata']
  });

  **if** (states.length *>* 0) {
    document.getElementById('pd').innerHTML *=* '<h3><strong>' *+* states[0].properties.name *+* '</strong></h3><p><strong><em>' *+* states[0].properties.density *+* '</strong> people per square mile</em></p>';
  } **else** {
    document.getElementById('pd').innerHTML *=* '<p>Hover over a state!</p>';
  }
});
For map.on(‘mousemove’) you’ll need to make the following changes, to reflect the different fields in the canada-pop data:
map.on('mousemove', function(e) {
  var provinces *=* map.queryRenderedFeatures(e.point, {
    layers: ['canada-pop']
  });

  **if** (provinces.length *>* 0) {
    document.getElementById('pd').innerHTML *=* '<h3><strong>' *+* provinces[0].properties.NAME *+* '</strong></h3><p><strong><em>' *+* provinces[0].properties.aboriginal_pop *+* '</strong>Aboriginal population</em></p>';
  } **else** {
    document.getElementById('pd').innerHTML *=* '<p>Hover over a province!</p>';
  }
});
**Map bounds**
If you want to set the map bounds to focus on Canada and include the far North, instead of:
map.fitBounds([[*-*133.2421875, 16.972741], [*-*47.63671875, 52.696361]]);
You’ll want something like: 
map.fitBounds([[-188.0859375, 37.1603165], [-30.5859375, 83.3595113]]);
(The [lng, lat] coordinates are found using [geojson.io](http://geojson.io/) - you can learn more about restricting map panning [here](https://www.mapbox.com/mapbox-gl-js/example/restrict-bounds/))
**Map title and info window**
Remember to change the text from US to Canada, state to province, ‘population density’ to ‘Aboriginal population’ etc.
**Option 2: Start from scratch**
If you didn’t attend the Mapbox Studio session, or don’t like choropleths, you can try a few different things (with the sample data linked in the tutorials):

  1. Add points to a map with pop-ups: [https://www.mapbox.com/studio-manual/help/#add-points-to-a-map](https://www.mapbox.com/studio-manual/help/#add-points-to-a-map) 
  2. Make a heatmap: [https://www.mapbox.com/help/make-a-heatmap-with-mapbox-gl-js/](https://www.mapbox.com/help/make-a-heatmap-with-mapbox-gl-js/) 
  3. Experiment with other things in the Mapbox GL JS examples library! [https://www.mapbox.com/mapbox-gl-js/examples/](https://www.mapbox.com/mapbox-gl-js/examples/) 

## 2017 IMW Session

**External Resources**
[https://api.mapbox.com/mapbox-gl-js/v0.40.0/mapbox-gl.css](https://api.mapbox.com/mapbox-gl-js/v0.40.0/mapbox-gl.css) 
[https://api.mapbox.com/mapbox-gl-js/v0.40.0/mapbox-gl.js](https://api.mapbox.com/mapbox-gl-js/v0.40.0/mapbox-gl.js) 
**Workshop**
We’re going to use a code editing tool called jsFiddle to add a simple toggle and hover-over information to make our map interactive, so it will look like this (screenshot is after hovering the mouse over the Northwest Territories): 

![Screen Shot 2017-10-20 at 4.07.53 PM.png](https://lh4.googleusercontent.com/jpbI0HRd4CbCJj1f-z8YjVHShT2SHExSW6m6LmsjPTj628E-QyMnC4LbOhn05O16WlY-INaoybZtofT-8aXMx9Vc55D5v3ltGQ1UT-iDDbZa-y_m-bx3SmiOb6UrVXbI7NnDYK3w)


The following links are shared from Alex’s jsFiddle account - you can work with them but you **can't save your edits** (otherwise everyone's work would change). Instead, use the button in jsFiddle that says `Run` - this lets you continually rerun your code to get your updates. **Don’t close your tab until you are completely finished**, or you will lose your edits!
Incomplete one to work with: [https://jsfiddle.net/aparlato/ebpqc82y/2/](https://jsfiddle.net/aparlato/ebpqc82y/2/)
Complete one for reference: [https://jsfiddle.net/aparlato/2oondv1u/](https://jsfiddle.net/aparlato/2oondv1u/) 


