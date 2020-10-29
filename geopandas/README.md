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

#### for example we can use these functions in geopandas , for example :- 

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
     points = count.apply(lambda row : Point(row.ongitude,latitude),axis=1)
```
step 3 <br>
- We create a new **GeoDataframe** and assoicate the points to it and Points format <span style="font-weight: bold">(Geo Coordinate Format)
</span> by assining  `{'init':'epsg:4326'}` to crs field  ***more about EPSG later***.

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

---









***EPSG code stand for "European Petroleum Survey Group"***

***CRS stand for Coordnate Reference System***

[CRS Reference ](https://docs.qgis.org/3.10/en/docs/gentle_gis_introduction/coordinate_reference_systems.html)


when we create a new GeoPandas df or shp files , we have to feed it with correct and apporpiate EPSG code , we can do it by this way 

```python 

geo_dataframe.to_crs(epsg=5071)

```

Each country , state , city may have thier own code , so we have to find a correct code from the below reference  



[epsg reference ](http://epsg.io/)

---

## Customizing the map 

### for resizing the map we pass the **figsize** in plot function 


where the frist number is width and second number is height .

```python

geo_dataframe.plot(figsize=(20,20))

```

### Removing the X,Y axis 

1- we save the plot as a variable 

```python
    ax = geo_dataframe.plot(figsize=(20,20))
    ax.axis('off')
```


### customizing the shape  
- filling(color) (inside the map ) 
- stroke/line/edge (edgecolor) (outside the map )
- line width 

#### Example 

***We can use Hex values too***

for `linewidth` we can go below 0 for example `0.25`

```python
ax = data.plot(figsize=(20,20),color='blue',edgecolor='red',linewidth=5)

```

### customizing the Points & Markers 

- change the property `markeredgecolor` to any color for 
- change the property `markeredgewidth` to any width
- change the properth `markersize` to change the size of marker . 
-we can control the transparancy of marker by adjusting the `alpha` value 



Example :- 

```python

ax = data.plot(figsize=(20,20),color='green',markeredgecolor='red',markeredgewidth=3,markersize=2,alpha=0.3)


```

---

## displaying the portion of shape 

- first we enable the grid in geo dataframe 

```python 
ax = data.plot(figsize=(20,20),color='grey',edgecolor='grey',linewidth=0.8)
ax.axis('on')
```

- then we select the portion of the shape in Y and X coordnate 

```python
ax.set_xlim(254000,256000)
ax.set_ylim(2700,2704)

```




