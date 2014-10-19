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
#cairo_pdf("ggmap2.pdf", width=6, height=6)
qmap("seoul", zoom = 11, source = 'osm')

# Stamen with Toner type
#cairo_pdf("ggmap3.pdf", width=6, height=6)
qmap("seoul", zoom = 11, maptype = 'toner', source = 'stamen')

# Stamen with watercolor type
#cairo_pdf("ggmap4.pdf", width=6, height=6)
qmap("seoul", zoom = 11, maptype = 'watercolor', source = 'stamen')
```
