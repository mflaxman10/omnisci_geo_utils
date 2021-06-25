# Purpose

This repo is designed to package utilities for geoML work with OmniSci into a pip or conda-installable library.

## Raster Import

-  OmniSci 5.6 does not support direct read of raster geoimagery or similar datasets.
-  However, these data can be represented internally as points or arrays.
-  The array representation is most efficient, since it avoids having to explicitly generate coordinates for each pixel.
-  But the point representation allows for rendering, whereas arrays currently do not.

## Multidimensional Arrays (MDA)

- These come in a variety of container-like file formats (netCDF, GRIB, etc)
- Usually, two dimensions represent geospatial coordinates in decimal degrees
- Time is typically represented as a third dimension
- Finally, various sensors or sensor-bands are represented as other dimensions.
- In OmniSci, a natural representation is often using simple rectangles as pixels, and encoding sensor dimensions as attributes
- In the specific case of forecast data, such as weather forecasts, it becomes important to distinguish and separately track "issue datetime" from "prediction datetime"

## LIDAR Data

- This is distributed typically in unique formats - LAS and LAZ
- We can use the PDAL library to read these formats and convert to 3d points
- At the same time, we can perform some common pre-processing steps, such as computing "height above ground"

