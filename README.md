# Durden
A tiling module, that's used to layer a geographic area with equal-area tiles. The tiles are created based on the utm coordinate system. As a result of using this system, the tiler will be abel to operate only within a latitude range beween 84 to -80 degrees, with some issues around Norway. 

The module holds 3 main classes:

## Classes
###  Tile
A single tile, has a completely desctiptive ans unique name and gemetry. Tiles are a part of a grid defined by scale or a tile size, and are describe using a row an a column within this grid.
Tile name are of the following from:

{utm_zone}{letter}r{row}c{col}s{tile_size_m}. Example: 36Sr40c30s12km.


A Tile is created and used in the following way:


```python
from durden.tile import Tile

lon = 45 #deg
lat = 34 #deg
grid_size_m = 12500 # meters

new_tile = Tile(lon, lat, grid_szie_m)

tile_geometry = new_tile.geometry()
```

### Grid
Each grid size will describe a different devision of the earth into equi-area tiles. This class creates and represents a subsection of this grid that is within a given AOI. The class also lends access to the tiles in several froms.

The grid is created like so:
```python
from durden.grid import Grid
from shapely.geometry import Polygon

AOI = Polygon([[0, 0], [10, 0], [10, 10], [0, 10], [0, 0]])

new_grid = Grid(AOI, gird_size_m=12000)
# Or: new_grid = Grid(AOI, scale=1.0). Default grid size = 25600

grid_geo_dataFrame = new_grid.tile_gdf()

```
 
 ### Zone
 represents A utm zone