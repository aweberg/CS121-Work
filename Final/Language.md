FINAL EXAM
===========


```r

require(mosaic)
```

```
## Loading required package: mosaic Loading required package: grid Loading
## required package: lattice
## 
## Attaching package: 'mosaic'
## 
## The following objects are masked from 'package:stats':
## 
## D, IQR, binom.test, cor, cov, fivenum, median, prop.test, sd, t.test, var
## 
## The following object is masked from 'package:base':
## 
## max, mean, min, print, prod, range, sample, sum
```

```r
fetchData("COMP121/word-hints.R")
```

```
## Retrieving from http://www.mosaic-web.org/go/datasets/COMP121/word-hints.R
```

```
## [1] TRUE
```

```r
require(plyr)
```

```
## Loading required package: plyr
## 
## Attaching package: 'plyr'
## 
## The following object is masked from 'package:mosaic':
## 
## count
```



```r

letterProportion <- function(v) {
    b <- strsplit(v, "")
    c <- unlist(b)
    d <- tolower(c)
    e <- table(d)
    a <- c()
    for (k in 1:length(unique(d))) {
        a <- c(a, e[[k]]/nchar(v))
    }
    f <- data.frame(letter = names(e), freq = a)
    return(f)
}

letterProportion("hello")
```

```
##   letter freq
## 1      e  0.2
## 2      h  0.2
## 3      l  0.4
## 4      o  0.2
```

```r
hello <- letterProportion("hello")

freqCompare <- function(v, w) {
    a <- data.frame(English, letter = names(English))
    b <- join(v, a)
    diff <- abs(b[2] - b[3])
    c <- (diff^2)/b[3]
    return(c)
}

freqCompare(hello, English)
```

```
## Joining by: letter
```

```
##   English
## 1 0.04804
## 2 0.42961
## 3      NA
## 4 0.18318
```

```r
sum(freqCompare(hello, English))
```

```
## Joining by: letter
```

```
## [1] NA
```

```r

```
