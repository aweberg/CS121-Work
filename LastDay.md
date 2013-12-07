LAST DAY
==========


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
votes <- fetchData("COMP121/MinneapolisMayor-2013.csv")
```

```
## Retrieving from
## http://www.mosaic-web.org/go/datasets/COMP121/MinneapolisMayor-2013.csv
```

```r

names(votes) <- c("Precinct", "First", "Second", "Third", "Count")

small <- head(votes)
```



```r

countVotes <- function(v) {
    names <- as.character(unique(v[[2]]))
    list <- c()
    for (k in 1:length(names)) {
        total <- v[[2]] == names[k]
        list <- c(list, sum(total))
    }
    finish <- data.frame(names = names, total = list)
    inds <- order(finish[2], decreasing = TRUE)
    finish <- finish[inds, ]
    return(finish)
}

countVotes(votes)
```

```
##                           names total
## 1                  BETSY HODGES 28935
## 8                   MARK ANDREW 19584
## 4                   DON SAMUELS  8335
## 6                    CAM WINTON  7511
## 10           JACKIE CHERRYHOMES  3524
## 2                      BOB FINE  2094
## 15                    DAN COHEN  1798
## 18           STEPHANIE WOODRUFF  1010
## 12              MARK V ANDERSON   975
## 5                     undervote   834
## 11                    DOUG MANN   779
## 9                    OLE SAVIOR   693
## 17            ALICIA K. BENNETT   351
## 24                JAMES EVERETT   347
## 26   ABDUL M RAHAMAN "THE ROCK"   338
## 20         CAPTAIN JACK SPARROW   264
## 27                    TONY LANE   219
## 23                   MIKE GOULD   204
## 3               KURTIS W. HANNA   200
## 13                 JAYMIE KELLY   196
## 19            CHRISTOPHER CLARK   188
## 35  CHRISTOPHER ROBIN ZIMMERMAN   170
## 28          JEFFREY ALAN WAGNER   164
## 31             TROY BENJEGERDES   148
## 7                   NEAL BAXTER   145
## 29             GREGG A. IVERSON   144
## 21                          UWI   117
## 16                   JOSHUA REA   108
## 30             MERRILL ANDERSON   108
## 22          JOHN LESLIE HARTWIG    97
## 37                    BILL KAHN    97
## 36                     overvote    93
## 14       EDMUND BERNARD BRUYERE    70
## 38             RAHN V. WORKCUFF    65
## 33 JAMES "JIMMY" L. STROUD, JR.    64
## 25        BOB "AGAIN" CARNEY JR    56
## 32                   CYD GORMAN    39
## 34          JOHN CHARLES WILSON    37
```


