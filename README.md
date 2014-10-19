GoogleMap
========
Modified R functions in package `ggmap` for using watercolor of Stamen. 
I have modified function `get_stamenmap` in the package `ggmap`.
Since original function would download `png` tiles  at Stamen webpage,
R shows error message such as 
```coffee
Error in readPNG("ggmapFileDrawer/ggmapTemp.png") : 
  file is not in PNG format
```
Actual reason of this error is that Stamen with watercolor type 
does not use `png` but `jpg` format.  Therefore I have changed two points.
One is destination file format (`png` -> `jpg`) and the other is load function of image (`readPNG` -> `readJPG`).
### Load the source code

```coffee
gitaddress <- "https://raw.githubusercontent.com/dongikjang/GoogleMap/"
# load the source code
library(RCurl)
u <- paste(gitaddress, "master/StamenWatercolor.R", sep="")
eval(parse(text = getURL(u, followlocation = TRUE, 
                         cainfo = system.file("CurlSSL", "cacert.pem", 
                                              package = "RCurl"))), 
     envir = .GlobalEnv)
```

### An example
```coffee
library(ggmap)
library(jpeg)
library(png)
library(plyr)

# Hybrid Map of Google Maps
qmap("seoul", zoom = 11, maptype = 'hybrid')

# Openstreet Map
qmap("seoul", zoom = 11, source = 'osm')

# Stamen with Toner type
qmap("seoul", zoom = 11, maptype = 'toner', source = 'stamen')

# Stamen with watercolor type
qmap("seoul", zoom = 11, maptype = 'watercolor', source = 'stamen')
```
