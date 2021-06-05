# rasters

- [PlaceCount Rasters](https://github.com/chapmanjacobd/rasters/blob/main/osm/README.md)

- pop.tif Derived from WorldPop 2020

  ```sh
  gdalwarp -dstnodata 0 -t_srs EPSG:3857 -tap -tr 1912.0 1912.0 -ot Int32 -r sum -co COMPRESS=DEFLATE ./ppp_2020_1km_Aggregated.tif ./pop.tif
  gdal_edit.py -unsetnodata ./pop.tif
  ```

  WorldPop (www.worldpop.org - School of Geography and Environmental Science, University of Southampton; Department of Geography and Geosciences, University of Louisville; Departement de Geographie, Universite de Namur) and Center for International Earth Science Information Network (CIESIN), Columbia University (2018). Global High Resolution Population Denominators Project - Funded by The Bill and Melinda Gates Foundation (OPP1134076). https://dx.doi.org/10.5258/SOTON/WP00647 Creative Commons Attribution 4.0
