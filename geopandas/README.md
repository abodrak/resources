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

### we can some built in pandas functions in geopandas 

#### for example we can these functions in geopandas , for example :- 

- ` data.head()`
-  ` data[data.colum_name > 100000]`

<br>
<br>

### Creating Geodataframe from pandas dataframe 
<br>

#### for creating geodata frame from pandas df , the original pandas dataframe must have latitude and longituide columns . 
<br>
step 1 , <br>

-  import the nessesary libraries 

```python
import pandas as pd
from shapely.geometry import Point 
import geopandas as gpd
```


- We create a Points assoicated with 2 longitude latitude data from pandas dataframe by using simple lambda function 




```python 
     points = count.apply(lambda row : Point(row. usa_state_longitude,row.usa_state_latitude),axis=1)
```


