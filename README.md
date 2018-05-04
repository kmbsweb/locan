# locan
ggplot2でshapefileを表示するためにはデータフレームclassに変更する必要がある。Spatial Polygon Data FrameからData Frameに変換する関数を格納している。

## Installation

```R
# Not CRAN Package
# Development version only
devtools::install_github("kmbsweb/locan")
```   
    
## Examples
和歌山県の市区町村を塗り分ける。

```R
# read the package
library(locan)
library(raster)
library(dplyr)
library(ggthemes)
library(ggplot2)

# retrieve shp.file from raster
m <- getData("GADM", country="Japan", level=2)
m <- m[m$NAME_1 %in% c("Wakayama"),]

Wakayama <- shptogf(m)

# plot
ggplot() +
  geom_polygon(data=Wakayama, aes(x=long, y=lat, group=group,fill=NL_NAME_2)) +
  labs(title="") +
  theme_map() 
``` 

![proxies](https://github.com/kmbsweb/locan/blob/master/pic/test1.PNG?raw=true)
