GoogleMap
========
R functions for using watercolor of Stamen

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
