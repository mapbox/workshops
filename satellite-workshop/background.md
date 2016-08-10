# Analyzing the Earth using Earth Observation data

![untitled2](https://cloud.githubusercontent.com/assets/126868/16667445/24493b76-44aa-11e6-9c7f-96278c2f829d.gif)<br>
_Combinations of spectral analysis over the [Mumbai landfill fire](https://www.mapbox.com/blog/mumbai-landfill-fire/) from Sentinel data_

[Earth Observation satellites](https://en.wikipedia.org/wiki/Earth_observation_satellite) regularly collect environment and surface data of the Earth, making a revisit over any part of the world evry 1-4 weeks. The satellites usually capture different wavelengths of the Sun's radiation reflected from the surface and atmosphere including the visible spectrum, infrared, shortwave and others that help identify various features not visible to the eye using spectral analysis.

## Data
* NASA Landsat-8/ESA Sentinel-2 Satellite search https://remotepixel.ca/projects/satellitesearch.html ([About](https://remotepixel.ca/blog/satellitesearch_20160610.html))
* [India] ISRO Oceansat-2/Resourcesat-1  http://bhuvan.nrsc.gov.in/data/download/index.php
* https://en.wikipedia.org/wiki/List_of_Earth_observation_satellites

## Bands
The data is collected in multiple bands, each capturing the reflected radiation of a certain wavelength from the Earth. Use [QGIS](http://www.qgis.org/en/site/) alongwith this [tutorial](https://github.com/mapbox/workshops/tree/gh-pages/satellite-workshop) to process the bands for analysis.

![](http://blog.imagico.de/wp-content/uploads/2016/07/sat_spectra_full3a.png)
_Comparison of multispectral EO satellites. From [what satellites see](http://blog.imagico.de/what-satellites-see/) by Cristoph Hormann_

### Landsat-8
![](http://landsat.gsfc.nasa.gov/wp-content/uploads/2015/06/Landsat.v.Sentinel-2.png)

[Band combinations](https://blogs.esri.com/esri/arcgis/2013/07/24/band-combinations-for-landsat-8/) | [Usage](http://landsat.usgs.gov/best_spectral_bands_to_use.php)

- Natural Color 4 3 2
- False Color (urban) 7 6 4
- Color Infrared (vegetation) 5 4 3
- Agriculture 6 5 2
- Atmospheric Penetration 7 6 5
- Healthy Vegetation 5 6 2
- Land/Water 5 6 4
- Natural With Atmospheric Removal 7 5 3
- Shortwave Infrared 7 5 4
- Vegetation Analysis 6 5 4

###Sentinel-2
<img width="1202" alt="screenshot 2016-07-09 01 04 44" src="https://cloud.githubusercontent.com/assets/126868/16699332/277277b4-4571-11e6-8e4f-b4d7fc045154.png">
_[Source](http://www.eurosdr.net/sites/default/files/images/inline/1-2dag_gascon_ws_sentinel.pdf)_

[Sentinel-2 Bands](https://earth.esa.int/web/sentinel/user-guides/sentinel-2-msi/resolutions/spatial) | [Specification](https://sentinel.esa.int/documents/247904/685211/Sentinel-2+Products+Specification+Document+%28PSD%29/0f7bedeb-9fbb-4b60-91aa-809162de456c)

- False Color [8 4 3](https://scientiaplusconscientia.wordpress.com/2016/02/11/working-with-sentinel-2-data-visualizing-and-exploring-with-snap/)
- Vegetation Health [6 5 3](http://www.sterlinggeo.com/news-articles/2016/01/07/a-look-at-the-new-sentinel-2a-data/): Healthy vegetation (red-orange)
- SWIR Fires [12 11 8a](http://www.geosage.com/highview/features_sentinel2.html)

## Processing and Analysis
Use one of these resources to start analyzing the bands from your data source:
- https://github.com/mapbox/workshops/tree/gh-pages/satellite-workshop
- https://www.mapbox.com/blog/putting-landsat-8-bands-to-work/
- http://landsat.gsfc.nasa.gov/?page_id=2372
- http://www.harrisgeospatial.com/Home/NewsUpdates/TabId/170/ArtMID/735/ArticleID/14305/The-Many-Band-Combinations-of-Landsat-8.aspx
- http://gisgeography.com/landsat-program-satellite-imagery-bands/
- http://www.bluecover.pt/wp-content/uploads/2014/03/paper-remote-sensing-with-satellite-open-data-nduro_ggoncalves-v1_0_accepted.pdf
- http://semiautomaticclassificationmanual-v4.readthedocs.io/en/latest/remote_sensing.html

**Theory**
- [Displaying and Stretching 16-bit per Band Digital Imagery - NASA](https://www.fsa.usda.gov/Assets/USDA-FSA-Public/usdafiles/APFO/support-documents/pdfs/film_vs_digital_linear_non-linear_stretches.pdf)
- [Sentinel-2 Data for Crop and Tree Species Classifications](http://www.mdpi.com/2072-4292/8/3/166/htm)
