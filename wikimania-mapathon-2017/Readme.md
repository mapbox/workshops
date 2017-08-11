## Mapathon! Contribute and connect OpenStreetMap and Wikipedia using Wikidata

13th August, 2017 | Wikimania Conference | [Workshop proposal](https://wikimania2017.wikimedia.org/wiki/Submissions/Mapathon!_Contribute_and_connect_OpenStreetMap_and_Wikipedia_using_Wikidata)

Presented by: mikel@mapbox.com and minh@mapbox.com

---

### Introduction to OpenStreetMap

[OpenStreetMap — free and open map of the entire world](https://www.openstreetmap.org/)

[![OSM](http://img.youtube.com/vi/7sC83j6vzjo/0.jpg)](https://www.youtube.com/watch?v=7sC83j6vzjo "OSM")


#### How does it work technically?

![image](https://user-images.githubusercontent.com/4470913/29123045-071973ce-7d32-11e7-8210-531a2fb83125.jpg)

### Who is OSM?

- Mappers

![image](https://user-images.githubusercontent.com/4470913/29123420-5532fd7c-7d33-11e7-9f13-403fdd3390a9.png)

- Companies 

![image](https://user-images.githubusercontent.com/4470913/29123462-74983538-7d33-11e7-9f6b-992280a24b1c.png)

- Governement

![image](https://user-images.githubusercontent.com/4470913/29123505-99e19d02-7d33-11e7-9df9-a2ba4899492d.png)

- Humanitarian OpenStreetMap Team

![image](https://user-images.githubusercontent.com/4470913/29123521-aa4c2fe0-7d33-11e7-984d-0118b9b3ed6d.png)

- Academics

![image](https://user-images.githubusercontent.com/4470913/29123581-e16eb164-7d33-11e7-9e11-a8922c605187.png)


#### Different OSM editors

- [iD editor](https://www.openstreetmap.org/edit?editor=id#map=16/45.4682/-73.5468)

![image](https://user-images.githubusercontent.com/4470913/29123848-b56bace2-7d34-11e7-82a1-06b555def06a.png)

- [JOSM editor](https://josm.openstreetmap.de/)

![image](https://user-images.githubusercontent.com/4470913/29123992-2b074830-7d35-11e7-84d9-5aca210235de.png)


### OSM <> Wikipedia/Wikidata connection


#### Introduction to adding Wikidata tags to OSM using iD editor 


- Go to iD editor - https://www.openstreetmap.org/edit?editor=id#map=19/45.49798/-73.57130
- Select the feature in OSM that you want to add a Wikipedia/Wikidata tag
	- Here I'll select the node - 'Le Centre Sheraton'
	- Check for existing Wikidata/Wikipedia tags

![image](https://user-images.githubusercontent.com/4470913/29125326-1d9a065c-7d39-11e7-8237-5ba0a1297cd2.png)


 - Type Wikipedia in `Add field` 
 - Choose the language you would like to add the information in from the dropdown, here, let us choose `English`
 - The dropdown below the language field will provide you with a link to the possible options, choose the relevant one. You can check the correctness of the options by clicking on the `hyperlink` button beside it.
  - In this case hyperlink should take you to - https://en.wikipedia.org/wiki/Le_Centre_Sheraton_Hotel

 ![image](https://user-images.githubusercontent.com/4470913/29141673-c7f0949e-7d6c-11e7-9e19-b046e72c56cd.png)

- Post selecting the option, you will find the tags associated to the features updated with the Wikidata and Wikipedia tags

![image](https://user-images.githubusercontent.com/4470913/29141732-0b66417e-7d6d-11e7-9bc5-4ac14cac7683.png)

_Before adding Wikipedia tag_


![image](https://user-images.githubusercontent.com/4470913/29141779-3cf571c4-7d6d-11e7-9050-34c5bedfeeb5.png)

_After adding the Wikipedia tag_

- Click on `Save` botton
- Add a relevant changeset comment and upload! 💥 
Changeset comment -> `Added wikipedia tag #wikimania2017`

![image](https://user-images.githubusercontent.com/4470913/29141851-8f517c24-7d6d-11e7-9f4b-4d81d9bdc46f.png)

### Introduction to using Kartographer extension

#### How to embed maps in Wikipedia articles using kartographer extension


- More information on Kartographer extension - https://www.mediawiki.org/wiki/Help:Extension:Kartographer

Note: Does not work on English Wikipedia but works on Wikivoyage language editions, including the Swedish Wikipedia and English Wikivoyage. 

- Go to a wikipedia/wikivoyage page (here -> https://en.wikivoyage.org/wiki/Montreal) and add the following syntax

```
<mapframe text="Montreal [[wikipedia:Montreal|Montreal]]" width=250 height=250 zoom=14 longitude=-73.6145 latitude=45.494445.4944 />

```

- Update the latitude, longitude and zoom levels of the map and save the edit
- This will embed the map anywhere in your wiki page.
- Changing `<mapframe>` to `<maplink>` creates a link to a full screen map

![image](https://user-images.githubusercontent.com/4470913/29143059-86212e7a-7d71-11e7-89ff-23825e25b157.png)

**Plotting Wikidata items**

- To highlight a geographical feature like a city outline or a highway, just add a reference to the Wikidata Qid in the mapframe.

```
<mapframe text="City of Montreal" width=300 height=300 zoom=9 longitude=-73.6386 latitude=45.5198>
{
  "type": "ExternalData",
  "service": "geoshape",
  "ids": "Q340"
}
</mapframe>
```

![](https://user-images.githubusercontent.com/126868/29207383-9b9bf6ee-7ea3-11e7-9210-e2684eab300c.png)

- This requires the Wikidata item to be mapped on the OpenStreetMap Project. You can check the already mapped Qids using the [OSM Overpass Query Service](http://overpass-turbo.eu/s/qVU) and add new ones using [OSM.Wikidata Link](https://osm.wikidata.link)
- You can right click on the map to get its coordinates and zoom to fine tune the view
- Explore more using [examples](https://en.wikipedia.org/wiki/User:Naveenpf/sandbox) and the [documentation](https://www.mediawiki.org/wiki/Help:Extension:Kartographer#External_data)

## How is Mapbox using OSM and Wikidata

- Multilingual map - https://mapbox.github.io/mapbox-gl-language/ 
![](https://d2mxuefqeaa7sj.cloudfront.net/s_2B33C791A7F0CBCFA1594D29FFFDB1F8BA65211D86D19EF71B6A99524742BF65_1502204597521_image.png)
- Mapbox Geocoder - https://blog.mapbox.com/our-geocoder-wikipedia-126e9bf2f2bc
- Adding Wikidata translations - https://www.wikidata.org/wiki/User:Planemad_mapbox/World_places_translation_project
- Mapbox’s contribution in adding 100 thousand translations in the World place translation projects: https://www.wikidata.org/wiki/User:Planemad_mapbox/World_places_translation_project


## Other things that you can do!


### OSM <> Wikipedia/Wikidata connection for helping one find missing/incorrect information

**Find Wikidata items to map on OSM**

- Use https://osm.wikidata.link to review and match Wikidata features to OSM objects for your city


**Find Wikidata items to improve**

- Explain how these two open source projects help in finding out missing/incorrect information
- Click on this link → https://wiki.openstreetmap.org/wiki/Wikidata_RDF_database#Find_nodes_located_too_far_from_Wikidata.27s
- Go to → Find nodes located too far from Wikidata's section and click on `Run this`  which will take you here: http://tinyurl.com/ydfbbtd3
![](https://d2mxuefqeaa7sj.cloudfront.net/s_2B33C791A7F0CBCFA1594D29FFFDB1F8BA65211D86D19EF71B6A99524742BF65_1502196560162_image.png)

- Running this query will result in OSM Ids, Wikidata Ids and the distance between them.
  - Based on the distance you can inspect and find out which of the two (OSM or Wikidata) has erroneous data.
  - Click on the OSM link to inspect the object 
  - Click on the Wikidata link to check the data 
  - Based on the inspection, you can understand if the location of OSM feature or Wikidata has an error or so.


 ## Resources

- [LearnOSM](http://learnosm.org/en/) will help you get started with OpenStreetMap
- [Mapping guides](https://www.mapbox.com/mapping/)
- [OpenStreetMap Forum](https://forum.openstreetmap.org/) - please feel free to post any questions you have
- [OSM mailing lists](https://wiki.openstreetmap.org/wiki/Mailing_lists) - subscribe to talk-in and participate in various discussions
- [TagInfo](https://taginfo.openstreetmap.org/) - one place to find information about the tags used in OpenStreetMap


