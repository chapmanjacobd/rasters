# rasters

- [PlaceCount Rasters](https://github.com/chapmanjacobd/rasters/blob/main/osm/README.md)

- Ookla Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)

- pop.tif Derived from WorldPop 2020

  ```sh
  gdalwarp -dstnodata 0 -t_srs EPSG:3857 -tap -tr 1000 1000 -ot Int32 -r sum -co COMPRESS=DEFLATE ./ppp_2020_1km_Aggregated.tif ./pop.tif
  gdal_edit.py -unsetnodata ./pop.tif
  ```

  WorldPop (www.worldpop.org - School of Geography and Environmental Science, University of Southampton; Department of Geography and Geosciences, University of Louisville; Departement de Geographie, Universite de Namur) and Center for International Earth Science Information Network (CIESIN), Columbia University (2018). Global High Resolution Population Denominators Project - Funded by The Bill and Melinda Gates Foundation (OPP1134076). https://dx.doi.org/10.5258/SOTON/WP00647 Creative Commons Attribution 4.0

- Natural Earth boundaries

  ```
  wget https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_0_countries.zip
  unzip ne_10m_admin_0_countries.zip
  ogr2ogr ne_10m_countries.gpkg ne_10m_admin_0_countries.dbf -dialect sqlite -where "NAME != 'Antarctica' " -t_srs EPSG:3857

  wget https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip
  unzip ne_110m_admin_0_countries.zip
  ogr2ogr ne_110m_countries.gpkg ne_110m_admin_0_countries.dbf -dialect sqlite -where "NAME != 'Antarctica' " -t_srs EPSG:3857
  ```
