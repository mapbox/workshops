# Validating the map - Workshop Guide

![banner-image](https://user-images.githubusercontent.com/8921295/29491313-f7b3c83a-8592-11e7-82cd-0bdeb3fcb746.png)


This document is aimed to be a step-by-step guide to emulate and accompany the workshop of Validating the map conducted at [State of the Map, 2017](https://2017.stateofthemap.us/program/).


### Workshop Schedule - 75mins

- Introduction to validation - **5mins**
  - Validating changesets
  - History tab on OSM
  - Tools for Validation
- Introduction to OSMCha - **40mins**
  - UI walkthrough - OSMCha webpage
    - Sidebar
    - Panels
    - Changeset-map
  - Filters
   - Bbox search + size bound
   - Number of objects touched
   - Area of Interest - Saved filters + GeoRSS feed
  - Workflow
    - Rules for validation
    - Review :thumbsup: or :thumbsdown:
    - Review Tags
    - Changeset comments
  - OSM-Compare detections
  - Introduction to OSM-Compare functions
    - Example walkthrough
- Hands-on validation session - **20mins**
- Feedback & Questions - **10mins**




## Validating changesets



**Pointers**

Why validate changesets when we can validate features?

- Great for providing feedback to OSM users through changeset comments
- Process of validating changesets provides much more contextual information about the area, mapper and intent of the changeset compared to looking at individual feature edits
- Changesets are fewer, features are many



To understand a changeset and to validate a changeset, this is the minimum information a reviewer needs -


**Context of a changeset**

- Changeset metadata information
  - When and where a changesets has been committed to OSM
  - Editor, changeset comment
  - Source, Imagery used

**Edits**

- Map visualization
- History of features

**User context**

- User information and experience

### History tab on OSM

![History_tab_on_OSM](https://user-images.githubusercontent.com/8921295/29026274-9dd1b826-7b98-11e7-856a-9d8d6f49e785.png)

History in a bbox: https://www.openstreetmap.org/history?bbox=-99.3103,-65.4407,111.6272,76.8004

- We are provided with all changesets whose bboxes intersect with the provided bbox
- List of changesets on the left side bar
- Rendered map on the right

**Context of a changeset**

:white_check_mark: When and where a changeset has added map data

:white_check_mark: Editor, changeset comment

:white_check_mark: Source and Imagery used

**Edits**

:white_check_mark: History of features for properties

:negative_squared_cross_mark: Map visualization

:negative_squared_cross_mark: History of features for geometry

### Different tools for different use-cases - Tools for validation


- Changeset information - OSM Changeset Page
- User information - OSM User profile, [HDYC - ResultMaps](http://hdyc.neis-one.org/)
- History of feature tags - OSM Feature page, [OSM Lab Deep-History](https://osmlab.github.io/osm-deep-history/)
- Map visualization - [Achavi](wiki.openstreetmap.org/wiki/Achavi), [Changeset-Map](https://github.com/osmlab/changeset-map/)
- Changeset discussion - [OSM Contributor discussions - ResultMaps](http://resultmaps.neis-one.org/osm-discussions), [OSM-Comments](https://www.mapbox.com/osm-comments/)
- Filtering changesets - [OSM-Suspicious - ResultMaps](http://resultmaps.neis-one.org/osm-suspicious#2/8.2/26.2), [whodidit](http://simon04.dev.openstreetmap.org/whodidit/)
- Detection - [OSM-Suspicious - ResultMaps](http://resultmaps.neis-one.org/osm-suspicious#2/8.2/26.2), [OSM-Compare](https://github.com/mapbox/osm-compare)
- UserID based username retrieval - [Who's That](http://whosthat.osmz.ru/)



### OSMCha

OSMCha is short for OpenStreetMap Changeset Analyser.

![osmcha-image](https://user-images.githubusercontent.com/8921295/29361840-fc7d959c-82a6-11e7-9ee6-9bc7d2de883b.png)
_[About OSMCha](https://osmcha.mapbox.com/about)_

![coverage-2017](https://user-images.githubusercontent.com/8921295/29483788-d87fbd3c-84ea-11e7-9c25-90977db0dec8.png)
_Changesets validated in 2017 using OSMCha - [Coverage-map](https://manoharuss.github.io/coverage-map/)_



#### Few features in OSMCha

- Advanced Filters
- Contextual information
- Changeset-map
- Detections from OSM-Compare

Weblink: https://osmcha.mapbox.com/


#### UI Walkthrough

- Sidebar with list of changesets
- Panels for contextual information
- Changeset-Map
 - Geometric diff
 - Feature tags history: old  version and new version


#### Filters

![osmcha-filters](https://user-images.githubusercontent.com/8921295/29361780-af6529d2-82a6-11e7-9ddf-490e5d6e854c.png)

#### Few features

- Date bound search
- Bbox + Bbox size bound search
- Comment based search
- Prepared list of changesetIDs
- Number of objects touched
- Area of Interest - Saving Filters
  - GeoRSS feed
- [OSM-Compare](https://github.com/mapbox/osm-compare) detections

More information in the About page: https://osmcha.mapbox.com/about


### Workflow

#### Reviewing :thumbsup: or :thumbsdown:

Feature tag verification
- Compatible tag input vs feature type
- Minimum combination of feature tags added
- Contextual information in the area

Geometric verification
- Alignment to imagery
- Overlapping geometries
- Basic geometric errors

#### Review tags

- Severity assessment based on render zoom level on OSM
- Resolved and unresolved
- Intentional or unintentional
- DWG

#### Changeset comments

- Inviting new Contributors and encouraging to self correction and verify wiki
- Flagging experienced users on accidental edits
- Request sources for possible imports


### OSM-Compare detections

Theme based validation
- Null island edits - https://github.com/mapbox/osm-compare/blob/master/comparators/null_island.js
- Finding impossible angles in highways https://github.com/mapbox/osm-compare/blob/master/comparators/impossible_angle.js

**Detectors**

[mapbox/osm-compare](https://github.com/mapbox/osm-compare)

- Repository walkthrough
- Detector walkthrough -  Large building detector - https://github.com/mapbox/osm-compare/blob/master/comparators/large_building.js



### Repositories and links


- OSMCha-Frontend: https://github.com/mapbox/osmcha-frontend/

- OSMCha-django backend: https://github.com/willemarcel/osmcha-django

- API-docs: http://osmcha.mapbox.com/api-docs/
