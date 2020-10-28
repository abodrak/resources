# Geopandas resources 

## opening shapefile in jupyter notebook 


```python
import geopandas as gpd

data = gpd.read_file('data/data.shp')

```
### displaying the enteries for shapefile 

```python
data.head()
```


