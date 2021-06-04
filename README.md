# rasters

- PlaceCount Rasters

- pop.tif Derived from WorldPop 2020

  ```sh
  gdalwarp -tap -tr 1912.0 1912.0 -ot Int32 -r q3 -co COMPRESS=DEFLATE ppp.tif pop.tif
  ```

  WorldPop (www.worldpop.org - School of Geography and Environmental Science, University of Southampton; Department of Geography and Geosciences, University of Louisville; Departement de Geographie, Universite de Namur) and Center for International Earth Science Information Network (CIESIN), Columbia University (2018). Global High Resolution Population Denominators Project - Funded by The Bill and Melinda Gates Foundation (OPP1134076). https://dx.doi.org/10.5258/SOTON/WP00647 Creative Commons Attribution 4.0
