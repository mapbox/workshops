
All usefull data must be downloaded from https://s3-us-west-2.amazonaws.com/remotepixel-pub/data/IMW/IMW2018_QGIS_data_processing.zip

## Data
- Sentinel2 imagery on post tornado Alonsa, MB area ([ref](https://www.ctvnews.ca/canada/he-lived-a-full-life-man-77-dies-in-manitoba-tornado-1.4040722)). [Wikipedia](https://earth.esa.int/web/sentinel/user-guides/sentinel-2-msi)

<p align="left">
  <img width=500 src="https://user-images.githubusercontent.com/10407788/44471953-0ee40900-a5fb-11e8-8866-7afca772241d.jpg">
</p>


- Extract from Canada 2016 Census for Manitoba and Saskatchewan
  - `da.shp`: Dissemination Area [definition](http://www12.statcan.gc.ca/census-recensement/2011/ref/dict/geo021-eng.cfm)
  > Small area composed of one or more neighbouring dissemination blocks, with a population of 400 to 700 persons. All of Canada is divided into dissemination areas.
  - `population.csv`: 2016 Census extract for population number over Manitoba and Saskatchewan ([ref](#pre-processing))

## QGIS 
For this workshop I'm using QGIS 3.2.2 (Bonn) under MacOS, but you should be able to reproduce every steps with older QGIS version.

## QGIS plugins
- **Profile tool**
- **mmqgis**

Install plugins: 
- `Plugins > Manage and Install Plugin`
- Type `mmgis ` in the search bar 
- Select `mmgis` and click `Install`

<p align="left">
  <img width=500 src="https://user-images.githubusercontent.com/10407788/44466481-629c2580-a5ee-11e8-87cf-1cfbf231bf94.jpg">
</p>

<p align="left">
  <img width=500 src="https://user-images.githubusercontent.com/10407788/44466482-629c2580-a5ee-11e8-9299-54f7c9baeb12.jpg">
</p>


## 1. Import and visualize data in QGIS 

- `drag&drop` or use the `Browser` panel

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44465940-fb31a600-a5ec-11e8-8261-59b06c53454f.jpg">
</p>

- `Right click on the layer > Zoom to Layer`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44466738-0ab1ee80-a5ef-11e8-88df-715ecea1b7fa.jpg">
</p>


## 2. Basic imagery processing 

- Create NDVI (vegetation index) dataset ([Wiki](https://en.wikipedia.org/wiki/Normalized_difference_vegetation_index))
- Change data display
- Visualize profile

#### 2.1. NDVI
- `Raster > Raster Calculator` (top Menu)
- Write expression in `Raster calculator expression` (`(NIR - R)/(NIR + R)`, with `B08.tif` as `NIR` and `B04.tif` as `R`)

<p align="left">
  <img height=700 src="https://user-images.githubusercontent.com/10407788/44467100-0508d880-a5f0-11e8-870d-08bb775ced87.jpg">
</p>

#### 2.2. Data display

- `Right click on the layer > Properties > Symbology > Render type > Singleband pseudocolor`
<p align="left">
  <img height=700 src="https://user-images.githubusercontent.com/10407788/44467326-97a97780-a5f0-11e8-9480-9cd98ab54e09.jpg">
</p>

- Set min/max to `-1 to +1` (by NDVI definition)
- Choose Min Max color for `Color ramp`
- Click on `Classify`

<p align="left">
  <img height=500 src="https://user-images.githubusercontent.com/10407788/44467327-97a97780-a5f0-11e8-83a4-30c51fdba98d.jpg">
</p>

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44467569-3209bb00-a5f1-11e8-82d0-9eabebc6f4d2.jpg">
</p>

#### 2.3. Profile

- `Plugins > Profile Tool > Terrain profile` (top Menu)

Make sure to select `NDVI` layer (we created in step 2.1)
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44471080-28845100-a5f9-11e8-8340-b37e06a3e57e.jpg">
</p>
Note: See how the NDVI values are dropping when passing over the tornado track.

#### 2.4. Trace tornado track
- `Layer > Create Layer > New Shapefile Layer` (top Menu)

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44472258-cc6efc00-a5fb-11e8-82e8-5872c0963dfa.jpg">
</p>

- Select `Line` geometry type

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44472259-cc6efc00-a5fb-11e8-9b96-ebbf69ca59cf.jpg">
</p>

This will create an empty layer.

- Allow layer edition: `Right click > Toggle Editing` or `Layer > Toggle Editing` (top Menu)
- Start tracing `Add Line Feature` in the `Digitizing Toolbar` (`View > Toolbar > Digitizing Toolbar`)

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44472585-78184c00-a5fc-11e8-8fb6-6c855fe3311f.jpg">
</p>

- Finish tracing by doing a `Right click`

- Inspect the newly create feature
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44472759-cfb6b780-a5fc-11e8-8fa1-e331ce49e22e.jpg">
</p>


## 3. Census data

- Load and visualize data 
- Extract Manitoba limits data
- Merge Census CSV data with limits data
- Explore Expression filtering/calculator

Data pre-processing (Optional)
```bash
# Download Census CSV for Prairies
wget http://www12.statcan.gc.ca/census-recensement/2016/dp-pd/prof/details/download-telecharger/comp/GetFile.cfm?Lang=E&TYPE=CSV&GEONO=044_PRAIRIES

# Extract population data
cat 98-401-X2016044_PRAIRIES_English_CSV_data.csv | grep "\"Population, 2016\"" >98-401-X2016044_PRAIRIES_English_CSV_data_population.csv

# Extract CSV header 
head -n 1 98-401-X2016044_PRAIRIES_English_CSV_data.csv > header.csv

# merge header and population data
cat header.csv 98-401-X2016044_PRAIRIES_English_CSV_data_population.csv > population.csv
```

#### 3.1. Filter and Extract Census data

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44475981-7bafd100-a604-11e8-8486-99dc107e1718.jpg">
</p>

Each `DA` features has 3 attributes: 
  - **DAUID**: Dissemnination Area ID
  - **PRUID**: Province ID
  - **PRNAME**: Province Name

After loading the data, we want to create a new layer with only Manitoba DA.

- `Right click on layer > Open Attribute Table`

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44476789-d34f3c00-a606-11e8-81e2-45e69c8281d5.jpg">
</p>

- Click on `Select features using an expression`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44476845-fa0d7280-a606-11e8-967a-b24e0b90c692.jpg">
</p>

- Write expression `"PRNAME"='Manitoba'` and click `Select features`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44477526-ed8a1980-a608-11e8-8429-df7c6c834750.jpg">
</p>

- Save selection to a new Shapefile `Click right on layer > Export > Save Selected Features As...`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44477566-0a265180-a609-11e8-9741-11965925bfe6.jpg">
</p>

#### 3.2. Merge Census and DA
The Census data has population info for each DA but in the CSV the `DA` ID is called `GEO_CODE (POR)` 

- `MMQGIS > Combine > Attribute Join from CSV File`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44477709-68533480-a609-11e8-9145-f2aa029b14bf.jpg">
</p>

- Inputs:
    - `population.csv`
    - `GEO_CODE (POR)` for the CSV field
    - `Manitoba DA` as input layer (the one we created in 3.1)
    - `DAUID` joint layer attribute

<p align="left">
  <img width=300 src="https://user-images.githubusercontent.com/10407788/44477923-19f26580-a60a-11e8-9c12-2826adbd672e.jpg">
</p>

We now have a new layer with both info from `da.shp` and `population.csv`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44478069-84a3a100-a60a-11e8-9b70-2a9e21fa4dba.jpg">
</p>

#### 3.3. Calculate population density

- `Right click on layer > Open Table Attribute > Open Field Calculator`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44478240-114e5f00-a60b-11e8-8d31-f0ce6af01afa.jpg">
</p>

Note: 
- The Census data header being verry long, the population attribute in the shapefile is called `Dim_ Sex(`
- When importing the CSV data, QGIS didn't recognize the population value as integer but as string

The Population density equation is then: `to_int("Dim_ Sex(") / $area`
- `to_int` is a QGIS function to cast a value to integer
- `$area` is a QGIS special variable name pointing to the feature area
 
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44478280-2b883d00-a60b-11e8-801a-12aee7672f78.jpg">
</p>

#### 3.4. Display data

- `Right click on layer > Properties > Symbology > Graduated`
- Select `POPDENS` attibute
- Because the Population is maily centered in Winipegs, using `Quantile` mode will create better color distribution
- Click on `Classify`

<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44478549-0ba54900-a60c-11e8-8e3f-9d72d38704df.jpg">
</p>

*Manitoba population density map*
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44478753-92f2bc80-a60c-11e8-9777-3c19e3af7c32.jpg">
</p>


## 4. Imagery + Census
We now have a population dataset and the track of the Tornado we extracted for the Sentinel2 imagery, let's try to extract the total population number in the tornado surrounding area. 

- `MMQGIS > Combine > Spatial Join`
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44478881-fed52500-a60c-11e8-89a6-0fcc140516b0.jpg">
</p>

- Inputs: 
    - `tornado_track` is the target layer
    - Use `Intersects` as spatial operation 
    - Extract data from `manitoba_da.shp`
    - `Sum` intersecting value for `Dim_ Sec(` attribute

<p align="left">
  <img width=300 src="https://user-images.githubusercontent.com/10407788/44478975-3cd24900-a60d-11e8-82e1-c5dbcb142634.jpg">
</p>

Results: The tornado affected **2** DA affecting a maximum of 458 people.
<p align="left">
  <img width=700 src="https://user-images.githubusercontent.com/10407788/44479173-cbdf6100-a60d-11e8-9b99-012203d3ad39.jpg">
</p>


# Useful links 
- https://docs.qgis.org/2.18/en/docs/training_manual/index.html
- http://antonys.github.io/qgis-workshop/


# Mandatory Meme
<p align="left">
  <img width=700 src="https://media.giphy.com/media/8A7wNWLOJCTorwzGSq/giphy.gif">
</p>
