# Geopandas resources 

### Opening shapefile in jupyter notebook 


```python
import geopandas as gpd

data = gpd.read_file('data/data.shp')

```
### displaying the enteries for shapefile 

```python
data.head()
```

### mapping & plotting the shape files 

```python
data.plot()
```

### we can use built in pandas functions in geopandas 

#### for example we can these functions in geopandas , for example :- 

- ` data.head()`
-  ` data[data.colum_name > 100000]`

<br>
<br>

---
<br>

### Creating Geodataframe from pandas dataframe 
<br>

#### for creating geodata frame from pandas df , the original pandas dataframe must have latitude and longituide columns . 
<br>
  <br>
step 1 <br>

- import the nessesary libraries 

```python
import pandas as pd
from shapely.geometry import Point 
import geopandas as gpd
```

step 2 <br>
- We create a Points assoicated with 2 longitude latitude cloumns from pandas dataframe by using simple lambda function , important thing to remember : **longitude** comes first when we reference colomns in lambda 




```python 
     points = count.apply(lambda row : Point(row. usa_state_longitude,row.usa_state_latitude),axis=1)
```
step 3 <br>
- We create a new **GeoDataframe** and assoicate the points to it and Points format <span style="font-weight: bold">(Geo Coordinate Format)
</span> by assining  `{'init':'epsg:4326'}` to crs field .

```python
g_df = gpd.GeoDataFrame(count,geometry=points)
g_df.crs = {'init': 'epsg:4326'}
g_df.head()
```

step 4<br>
- we can now plot the geo dataframe we created 

```python
g_df.head()
```
<br>