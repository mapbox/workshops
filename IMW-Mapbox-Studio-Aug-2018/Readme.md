# Mapbox Studio - Ooh Colours!

**→ First - create a free Mapbox account at** https://www.mapbox.com/signup/

If you have a Mapbox account, log in, if not sign up for Mapbox. It’s totally free to sign up.
**→ Introduction to Mapbox Studio (how and why to use this?)**

- Create a [static map](https://www.mapbox.com/help/how-static-maps-work/)
- Create a style for a basemap in [QGIS, Tableau, or other tools](https://www.mapbox.com/help/mapbox-arcgis-qgis/)
- [Create a style](https://www.mapbox.com/help/how-map-design-works/#how-map-styles-work) for a basemap for a dynamic, [interactive web map or app](https://www.mapbox.com/help/how-web-apps-work/)
- [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
- [Add data](https://www.mapbox.com/help/uploads/) to a style
- Make [beautiful custom styles](https://www.mapbox.com/designer-maps/)
- Use [dynamic styling rules](https://blog.mapbox.com/studio-expressions-design-81012e2dab55) (e.g. based on zoom level, based on field in the data etc.)

**→ Orientation to Mapbox Studio interface**

- Datasets, tilesets, and styles - oh my!
- Mapbox Studio Manual: [https://www.mapbox.com/studio-manual/overview/](https://www.mapbox.com/studio-manual/overview/)
- Mapbox Guide to Map Design: [https://www.mapbox.com/map-design/](https://www.mapbox.com/map-design/) 

**→ Hands-on exercise: We’re making a choropleth map!**
Definition: **Choropleth map:** a map that uses differences in shading, coloring, or symbols within predefined areas to indicate average values of a property or quantity in those areas.
**2018 IMW follow this tutorial:** [https://www.mapbox.com/help/choropleth-studio-gl-pt-1/](https://www.mapbox.com/help/choropleth-studio-gl-pt-1/) (Part 1)
(this is up to date with the latest changes in the Mapbox Studio interface)
Or for a more Canada-relevant choropleth, you can **use the datasets in the Mapbox folder on your USB** drive (for Canadian indigenous population data `canada-pop.geojson` and locations of First Nations reserves `first_nations_location.geojson`). The 2017 IMW instructions below show those datasets being used in basically the same tutorial as linked above.
**Tip**: Tool for picking colors: [http://colorbrewer2.org/](http://colorbrewer2.org/) 
**Tip**: Make sure that your `stops` in your data-driven styling make sense for the canada-pop data. I’d suggest something like this for your  `can-pop` layer:

![](https://lh4.googleusercontent.com/fwjd0kPlApn7uB6hF1ts500n8unPIcMwtgsv3Z3tc_G1Ay0OXWc0iEUIYbxMxR_3DZX_rTrMldBwNfLpJeHFcBxoMQDNada5lF3WBmEvcfcGZYc2i2RsUhNf7VUSZHdC5ivvBQML)


Tip: Don’t forget to **Publish** your style so you can use and share it!
Continue learning! [https://www.udemy.com/interactive-maps-with-mapbox](https://www.udemy.com/interactive-maps-with-mapbox/) 


# IMW 2017 Session

**Part A: Preparing our data**

1. Navigate to Mapbox Studio [](https://www.mapbox.com/studio/)[https://www.mapbox.com/studio/](https://www.mapbox.com/studio/)
2. Click on the Datasets tab on the left side of the screen
![](https://lh3.googleusercontent.com/d93PiF-F6Z8IsNyPAmiWUogOeuh1kqYETJOLJnN3tgKUtcQgYMVpMoTMS43d8iztIh9BjCYo0xjNwGgoXr6PTdtknGhSEg6nTSV9jXdXUdo4zgdvhA3QtGhqD-ETFL5mWkkjSOBX)



3. Click New Dataset
![](https://lh6.googleusercontent.com/MpybnmTwUNBiN8fWcyvHTHa5qOmFVEQEiPRlzPT6LdCIq4gOIkk9sdINKA7_3uo2QlMNiFELngWZmU2FaTfQK8qTwWNF6UX77y8ytRTFbSu3N7TFF1Iu_225XhfbmMm22MZhnSjQ)



4. Upload your dataset (we’ll be uploading two separate datasets, so we’ll be going through this twice)
![](https://lh4.googleusercontent.com/sNdhoT6ZGX-DD-BnrLZ1rl8xPt4FsKHyeSz4gz3KVBtsZGmpiQ6gwvpkIwTt5sF-S31wJkMTkVWJCibKnleqv4-yhydV2orekpI7-PN1ESd4pk-Z5Oa1caggDy9RVwyCC8y-XHjP)



- Choose file
- Hit Create
  - This creates the dataset from the geojson
  - We don’t need to edit, but hit Start editing to take a look at your data

**Part B: Adding data to a map style**

1. In the Dataset Editor (where we are), under Menu for the data we just uploaded, hit Export to tileset
![](https://lh3.googleusercontent.com/bFFduHQKA_sAg5ANFxLxow6ty0SkQbo4Qlh7NQsJtqVt4E-Mr2ppog6ulXSXi7ThCvlO1wamgLjI5A5-zOetPFzf-uf2tI2SI8KYnq46_8bewPcugJ9ciP6J_2XUqmL2EBbx-j1s)



2. Then go to your Tilesets
![](https://lh5.googleusercontent.com/n6zHxNaEU5wANcmB6F8IGybxuXWSHd3uNvrtIYLQSookZB-8C8qruObWTsgN_EdDhijx2HrCWvqPegoq0DvX0i_FzjYa5Pcp7DFmgHokwy-SuqUJ5s-iAwos5EEPVcDgbYzD9t7T)



3. Under Menu hit Add tileset to style
![](https://lh6.googleusercontent.com/GVBMfxsDj22dr3L5ntIxHSW7WnVeyFyyATkSGjT6AkmKvppP3QPmAbuCyoGlXY3hIWzBfsdA8zqPG8tRYJaFUSDsPPo2A0ntkVL720A9Yk31MonNuq6GEuK_lxpQ4KZgSFn-TPAK)



- Then choose New style
![](https://lh4.googleusercontent.com/Btb2wD2O5ZqevvPpKEkgRxdougHUMhWNjwlrnuilt87PsgkpTbegsJS2V1JkTpD_doyP5ubC14hn47eyqpmhMx5pUt-EYfcnCAvie-X2cfxNjQHUlo7H56Nhb5ueXfnHCuA2rRnP)



- Select a style (I chose Light) and hit Create
![](https://lh6.googleusercontent.com/TY6mbn_pJdIpdkoT3YqP8N64BiktPMXgmhFQTwQA-lU3cxdlyyUYT-4GKwTrWUR_cJ69F0tUTaDtUaX44uO17gBCZzc1e3zPN9p9IMVZIp_psA07eTU0Qkz_sGUK8DO7vD7aUcix)



- Hit Create layer
![](https://lh6.googleusercontent.com/EbSYuU5oNAJYCgY5hczr4F1xmYQ72ZVow3M2WImd9_TdI2Qbz5PgR_20z-cQgQmufd-iaZxFX4KsAQSzOnmYA36QaR722Rxdpd8f_AqwCnTDE7UcKPnm39oAXpiQh3Q2x4-zCRoB)


**Part C 1: Styling your data for a choropleth**

- Take a look at your data under the Select data tab and click a highlighted feature to see the properties in our data. We’ll be using aboriginal_pop as our data field for the choropleth map.
![](https://lh6.googleusercontent.com/2o_7hUB2PLCVl8Y0PIdo3MGFaNu3S3C-5S2MpKfvr6w3qBaJq5IRDSHPglJ_RCaY3YdvKYXhTKJ8fyZ2iak7QVoWv4va37LeNJvpHC_uxvkwuMd4c3oEbCV9r6g7KHDvbti5aXJ7)



- Under the Style tab go to your layer and click the menu button next to the color input and select Enable property function
![](https://lh3.googleusercontent.com/eIUGMQBycorV4j-VqYsHIRY-XPO5RKVRjGwz9-l29gBGOfFEzd5SdFZeUBzZt5RSu-zLeS07zlDp4eX-aB8xYxIVHySaNlbBccxomhDmtDSH11YvI4RtvEFSJXlJIo7tvp8EWENe)



- Under the field dropdown we see all of our data property fields we saw when viewing the data before. We want to select aboriginal_pop as the data we’re going to style by.
![](https://lh5.googleusercontent.com/JQgtQToPGE4j55DWck576uGJY3z8xR4jzkzrhQ163aUzuP98hCZJ7Y7Xj8GqZP86tk2unUM_7VEp46CDVpwAKOxPZxpme59bEBiu-TVuXU0Vd6aFoJLUq05SLI1FTZldki36r2dI)



- Now we can style our data. Choose the interval function type and add an appropriate number of stops with reasonable steps based on our data.
![](https://lh4.googleusercontent.com/puw5FBndGvYAVUDc76NsXoWGRfEtwI3q_KW5zylvufFi-bWYuPmtAtttP-EYYATlQ9TjJzRQTqR5b0xo4S_YVGqcDbLYQ1iDNyzK3jwL1K-t-lgYvjS0KvqfSLwrgiSRPxwqDrs4)

![](https://lh3.googleusercontent.com/9lzNF_DJy2v0baJzximanb8KxSlsBpiZx6bf7KxIEKrQpWmknQBcT7JuQIDpKPMw9dotHk1K1feJUKiD62IhgwRBgRZGLeALFWCX1iv4kqpYXOhalBF74PIHvv-43NHe1Kq0BCzU)



- Now you have a choropleth map! Let’s add the other data we brought in.
  - Since we already exported this data to a tileset we can just bring it in from our map style!
- Add a new Layer
![](https://lh3.googleusercontent.com/wtX7_hqf27U_qUQIRPn8j8_Js9DSj-fDdfcJcktlWf1SQ6Hkh_GVRTNiC1lQLdM5hgIHQQIA8x5LvJUg4sghGgHCiC9EFaLvEtqvGa-Nbg2ID9q6y7gTXcD4IHcnL9nYqtDtF-uF)


**Part C 2: Adding more information**

- Choose Source and select our second dataset
![](https://lh5.googleusercontent.com/QzjC7Gg--cpOJtsl3KcXvd1RHe1RYsAsbxpL3ksAyC9c50IFYv_FwVap8iFocrPL3e1cRa53_GcRRPcxyOrL2D-n2v09oh_Ddt6xBdo0bZF7xbjL-EUHmBP2nKzJOvBmp0JBebKA)



- Because this is point data it defaults to circle as a type so we want to switch that to symbol so we can use our own icons. Then go ahead and Create layer
![](https://lh4.googleusercontent.com/0zTXxG7dnb4cPnp2W8y6USKW2fTLRfb9TMQWkvDSc_t-_cecT06mbQoNL_f3G81YZt0Ng9VxdYXpoTfchnjryN2aLoGRfFPOBEvMsaS0l-a5891cJg_i8rLW0VTfVxRLris8k6OA)



- There should be nothing showing up because we haven’t selected any symbol yet. Select the Icon tab and then the Image input and select the icon you want. (If you’ve customized your own icon with our Maki Icon Editor or would like to and have dragged and dropped the svg file to the browser, then go ahead and use that!)
![](https://lh5.googleusercontent.com/ZtbNn4SKK0bbAU5MWBetMrOb7YmxvFjFgIVjkcjAWnBEjlYfhZsM-Atxonka-siOI9wjCDfeulBWoFjhTfM-wYh2LzNhlmuLFghFlC51TcHoXnLCA7kdTLanjNm9xNvz6Sejru79)

![](https://lh5.googleusercontent.com/goLk7G4r-10TFXQDh0T5pAIJj9v3uBK1ZMX4xOMl9rINNha-6nRdSodDbDqPq5i1dyFhIAA_dFwycPciTWqUum1um0m1m4YhvB3MU3b_bS2u_4G7FqofX-9K6qEegyGxWt49jmUO)



- Almost there! This isn’t really accurate to our data because Studio has a function that doesn’t let icons overlap because in many cases this is the best, most visually attractive option. For our purposes though we want to see every data point. Click the Placement tab and toggle on Allow icon overlap
![](https://lh6.googleusercontent.com/izuwWC_Qv8pppqJL9lWwRHpXkkcXnC4CssrWSBr9Ir-GDOKgndPHERfuXLAs2g-DET58Ervm53o8eEkf4OzHoXtEP-AyvrIkWgYa2aSWlZGYf3kX8xGJojFR-N_3hc8Af5ThrXof)



- That’s it!
![](https://lh4.googleusercontent.com/P8JBI2Q3X-ks1rq26YNYbsDx0Qp4PksfYTKCCpqU5wrftcglVVx0ic5d_24FOKeeLym_Uiw2L3rbWOkehgtId5sgj-xv-xnXtz3tqy6zTFTUQeR-fYBA3K6AWWi0Uw4pTMMql6-G)

- Now adjust the rest of the style as desired!
## **Reference links**
- Mapbox Studio Manual: [](https://www.mapbox.com/help/studio-manual/)[https://www.mapbox.com/help/studio-manual/](https://www.mapbox.com/help/studio-manual/)
- Mapbox GL Style Spec (top tabs for API and Examples): [](https://www.mapbox.com/mapbox-gl-js/style-spec/)[https://www.mapbox.com/mapbox-gl-js/style-spec/](https://www.mapbox.com/mapbox-gl-js/style-spec/)


