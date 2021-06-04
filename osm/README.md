# PlaceCount Rasters

Generated from OpenStreetMap -- June 1 2021

OpenStreetMap® is open data, licensed under the Open Data Commons Open Database License (ODbL) by the OpenStreetMap Foundation (OSMF).

The copyright portion of _this_ work (PlaceCount Rasters) is placed under Open Data Commons Public Domain Dedication and License (PDDL)

As seen on TV https://unli.xyz/city/calc/

## What is this

Counts of (groups of OSM tags/keys, specific tags, or specific keys) which are selected and currated by me.

## How to use

These are raw counts. To make them useful you'll likey want to do population-weighted statistics. Here is one way to do so:

### Using exactextract

https://github.com/isciences/exactextract

```sh
wget https://raw.githubusercontent.com/chapmanjacobd/rasters/main/ne_110m_countries.geojson
wget https://raw.githubusercontent.com/chapmanjacobd/rasters/main/pop.tif
wget https://raw.githubusercontent.com/chapmanjacobd/rasters/main/osm/walkable.tif.gz
gzip -d ./walkable.tif.gz

# NAME, ISO_A2, ECONOMY
exactextract -r pop:pop.tif \
  -r variable:walkable.tif \
  -p ne_10m_admin_0_countries.geojson \
  -f NAME \
  -s "sum(pop)" \
  -s "min(variable)" \
  -s "max(variable)" \
  -s "pop_weighted_mean=weighted_mean(variable,pop)" \
  -o countries-walkable.csv
```

#### Included Population (pop.tif) is WorldPop 2020

    WorldPop (www.worldpop.org - School of Geography and Environmental Science, University of Southampton; Department of Geography and Geosciences, University of Louisville; Departement de Geographie, Universite de Namur) and Center for International Earth Science Information Network (CIESIN), Columbia University (2018). Global High Resolution Population Denominators Project - Funded by The Bill and Melinda Gates Foundation (OPP1134076). https://dx.doi.org/10.5258/SOTON/WP00647 Creative Commons Attribution 4.0

#### For higher quality Geometry, try this

```
wget https://raw.githubusercontent.com/nvkelso/natural-earth-vector/master/geojson/ne_10m_admin_0_countries.geojson
ogr2ogr -t_srs EPSG:3857 ne_10m_countries.geojson ne_10m_admin_0_countries.geojson -skiperrors && rm ne_10m_admin_0_countries.geojson
```
