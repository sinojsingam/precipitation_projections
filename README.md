# precipitation_projections
Visualising future precipitation changes



# script workflow:

grid_fishnet.ipynb: generates the grid for Estonia's extent
raw_to_grid.ipynb: uses the grid and the netcdf files to extract precipitation values
static_map.ipynb: creates a static map with matplotlib
main.ipynb: creates the interactive webmap using folium
folium package generates html, the script from the html is taken and placed in index.js