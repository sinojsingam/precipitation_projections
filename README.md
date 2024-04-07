# Precipitation Projections
Visualising future precipitation changes in Estonia. [Visit the webmap](https://sinojsingam.github.io/precipitation_projections/).

## Description:
The “Temperature and precipitation climate impact indicators from 1970 to 2100 derived from European climate projections” dataset was obtained from the Copernicus Climate Data store. It is the resultant of a German global climate model and a Swedish RCA4 SMHI regional climate model. This precipitation dataset is originally presented for the whole of the European continent and in order to optimize the analysis of the projections for Estonia, the datasets had to be reduced and clipped to Estonia’s extent.

In order to obtain the netCDF observations for Estonia, a square grid that covered the country's extent with a grid resolution of 5 km, similar to that of the netCDF dataset, was generated. The grid was produced in the WGS84 reference system since the precipitation data had its location dimensions in decimal degrees.

Then, an algorithm went through the centroids of the custom grid and searched for the closest data point in the netCDF file using a squared distance formula. The resulting data value of mean precipitation was stored in a geopackage along with its corresponding grid location, the time period, and the RCP scenario. Thus, the values were successfully transferred from the raster netCDF to the vector grid cells.

The municipalities and major cities of Estonia were downloaded from the Estonian Land Board as a vector file, and were used for spatial aggregation of the raw data into mean values for each municipality, followed by obtaining those cities that fall within the 75th percentile of the precipitation values. Finally, the Folium API was used to generate an HTML page of the resulting data, from which the JavaScript code was extracted and placed in a javascript file for abstraction purposes.

## Script workflow:
1. grid_fishnet.ipynb: generates the grid for Estonia's extent
2. raw_to_grid.ipynb: uses the grid and the netcdf files to extract precipitation values
3. static_map.ipynb: creates a static map with matplotlib
4. main.ipynb: creates the interactive webmap using folium
5. folium package generates html, the script from the html is taken and placed in index.js
