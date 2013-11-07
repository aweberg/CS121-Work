Halloween
=======

```r

require(devtools)  # install if necessary
```

```
## Loading required package: devtools
```

```r
install_url("http://dtkaplan.github.io/ScientificComputing/Resources/COMP121_0.1.tar.gz")
```

```
## Downloading COMP121_0.1.tar.gz from
## http://dtkaplan.github.io/ScientificComputing/Resources/COMP121_0.1.tar.gz
## Installing package from /tmp/Rtmp4xvVsu/COMP121_0.1.tar.gz Installing
## COMP121 '/usr/lib/R/bin/R' --vanilla CMD INSTALL '/tmp/Rtmp4xvVsu/COMP121'
## \ --library='/home/aweberg/R/x86_64-pc-linux-gnu-library/3.0' \
## --with-keep.source --install-tests
```

```r
require(COMP121)
```

```
## Loading required package: COMP121 Loading required package: jpeg Loading
## required package: png Loading required package: RCurl Loading required
## package: bitops Loading required package: markdown
```

```r

puzzleURL <- "http://www.vistax64.com/attachments/chillout-room/9404d1231736689-spot-difference-spot02-c.jpg"
puzzle <- readJPEG(getURLContent(puzzleURL))


# ===============

readImageURL <- function(URL) {
    isJPEG <- grepl("[.jpg$|.jpeg$]", URL)
    
    if (isJPEG) 
        image <- readJPEG(getURLContent(URL)) else image <- readPNG(getURLContent(URL))
    
}
readImageURL(puzzleURL)
# ===============
splitThePuzzle <- function(puzzle) {
    sz <- dim(puzzle)
    mid <- sz[2]/2
    left <- puzzle[, 1:mid, ]
    right <- puzzle[, (mid + 1):sz[2], ]
    return(list(left = left, right = right))
}


# ================

# Generate a plane of colors

## Utility Functions
ShowImage <- function(image) {
    size <- dim(image)
    canvas(x = c(1, size[2]), y = c(1, size[1]), asp = 1)
    rasterImage(image, 1, 1, size[2], size[1])
}

planeBind <- function(red, green, blue) {
    array(c(red, green, blue), dim <- c(dim(red)[1], dim(red)[2], 3))
}
# ==========================
colorPlane <- function(npixels = 50, howMuchBlue = 0.5) {
    
    x <- seq(0, 1, length = npixels)
    
    # initialize state
    red <- matrix(0, nrow = npixels, ncol = npixels)
    for (k in 1:npixels) {
        # update
        red[, k] <- cbind(x)
    }
    
    green <- matrix(0, nrow = npixels, ncol = npixels)
    for (k in 1:npixels) {
        green[k, ] <- rbind(x)
    }
    
    blue <- matrix(howMuchBlue, nrow = npixels, ncol = npixels)
    
    return(planeBind(red, green, blue))
}

ShowImage(colorPlane(howMuchBlue = 0.5, npixels = 50))
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 
