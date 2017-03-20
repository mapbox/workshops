# Preparation step

## Downloading OSM data


http://download.geofabrik.de/europe/germany/bayern/niederbayern.html

```sh
mkdir -p ~/data && cd ~/data
wget http://download.geofabrik.de/europe/germany/bayern/niederbayern-latest.osm.pbf
```

*** Setting up the osrm-backend Docker image

https://hub.docker.com/r/osrm/osrm-backend-ci/

```sh
docker pull osrm/osrm-backend-ci
```

In the docker image the current work directory will be mounted to /data

```sh
docker run -v $(pwd):/data osrm/osrm-backend-ci ls /data
```


# OSRM toolchain


1. Extraction step converts OSM data using a Lua profile file into a set of OSRM files

```sh
docker run -v $(pwd):/data osrm/osrm-backend-ci osrm-extract -p /opt/car.lua /data/niederbayern-latest.osm.pbf
```

2. Contraction step augments the base graph with Contraction Hierarchies

```sh
docker run -v $(pwd):/data osrm/osrm-backend-ci osrm-contract /data/niederbayern-latest.osrm
```

3. Run an OSRM server with pre-processed OSRM files

```sh
docker run -v $(pwd):/data -p 5000:5000 osrm/osrm-backend-ci osrm-routed /data/niederbayern-latest.osrm
```

Now you can a routing query
```sh
curl "http://localhost:5000/route/v1/driving/13.449374,48.566477;13.460645,48.574014" | jq .
```

```json
{
  "code": "Ok",
  "routes": [
    {
      "geometry": "oslgHuyaqAgBEyBqGqAkHeDyGcCmG[yAmAsJmAgEsDhEiBcEyCkDeDnIe@\\]@AqA]gC`BoFmBeBZoA",
      "legs": [
        {
          "steps": [],
          "distance": 1640,
          "duration": 273.7,
          "summary": "",
          "weight": 273.7
        }
      ],
      "distance": 1640,
      "duration": 273.7,
      "weight_name": "routability",
      "weight": 273.7
    }
  ],
  "waypoints": ...
}
```

# OSRM frontend

OSRM frontend https://github.com/Project-OSRM/osrm-frontend
can be used to visualize route requests.

## Clone repository
```sh
mkdir ~/osrm-frontend && cd osrm-frontend
git clone https://github.com/Project-OSRM/osrm-frontend
```


## Change routing requests to the local OSRM server

In file `~/osrm-frontend/src/leaflet_options.js`
```
L31:  services: [{
L32:    label: 'Car (fastest)',
L33:    path: 'https://router.project-osrm.org/route/v1'
L34:  }],
```

`path` should be changed to 'http://localhost:5000/route/v1'

## Change debug tiles requests to the local OSRM server (optional)

In file `~/osrm-frontend/debug/index.html`
```
L126:        "osrm": {
L127:            "type": "vector",
L128:            "tiles" : ["http://router.project-osrm.org/tile/v1/car/tile({x},{y},{z}).mvt"]
L129:        }
```
`"tiles"` should be changed to `http://localhost:5000/tile/v1/car/tile({x},{y},{z}).mvt`

## Running OSRM frontend server

```sh
npm install && npm start
```

OSRM frontend should connect to the backend and show the path
http://localhost:9966/?z=16&center=48.570360%2C13.457887&loc=48.566477%2C13.449374&loc=48.574014%2C13.460645&hl=de&alt=0


# OSRM v5.6 API

Documentation at http://project-osrm.org/docs/v5.6.0/api/

OSRM request schema:
```
/{service}/{version}/{profile}/{coordinates}[.{format}]?option=value&option=value
```

Services:
1. Route service `/route/` finds the fastest route between coordinates in the supplied order.
2. Nearest service `/nearest/` snaps a coordinate to the street network and returns the nearest `n` matches.
3. Table service `/table/` computes the duration of the fastest route between all pairs of supplied coordinates.
4. Match service `/match/` matches given GPS points to the road network.
5. Trip service `/trip/` solves the Traveling Salesman Problem using.
6. Tile service `/tile/` generates Mapbox Vector Tiles that can be viewed with a vector-tile capable slippy-map viewer.

# Understanding profiles

Wiki link https://github.com/Project-OSRM/osrm-backend/wiki/Profiles

```
function node_function (node, result)
```

```
function way_function(way, result)
```

```
function turn_function (turn)
```

```
function segment_function (segment)
```

# Copying profiles from Docker container

First you need to copy profile files to a local directory:
* check Docker container ID
```
$ docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED              STATUS              PORTS                    NAMES
83c3c815d21b        osrm/osrm-backend-ci   "osrm-routed /data/ni"   About a minute ago   Up About a minute   0.0.0.0:5000->5000/tcp   zen_brattain
```
* and copy profile files to a local directory
```
$ docker cp 83c3c815d21b:/opt ~/profiles/
```

# First Challenge: "Never Turn Left" routing

The shortest or fastest path routing is not always better. Accordingly to
http://bigthink.com/robby-berman/the-science-behind-why-ups-trucks-avoid-making-left-turns

> By keeping left-hand turns to a minimum, UPS says it’s saved 10 million gallons of fuel,
> avoided the emission of 20,000 tons of CO2, and delivered 350,000 more packages a year.

Modify in `car.lua` profile  `turn_function` to avoid left-turns in routing.

# Second Challenge: Make our cities green

Avoiding city centers in router can reduce air-pollution.

Modify in `car.lua` profile  `segment_function` to avoid routing through Passau city center.

# Third challenge (advanced): OSRM meets Mapillary

Map matching in Mapillary uses Meili by Mapzen http://blog.mapillary.com/update/2016/07/14/meili.html

Write a script that uses the Mapillary API and the OSRM matching service to
associate fetched photos with OpenStreetMap network.
