NOV 21
=======


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
DataExample <- KidsFeet[seq(1, nrow(KidsFeet), by = 4), c("sex", "width", "length", 
    "domhand")]

DataExample
```

```
##    sex width length domhand
## 1    B   8.4   24.4       R
## 5    B   8.9   25.1       R
## 9    G   9.3   23.6       R
## 13   B   9.1   26.1       R
## 17   G   8.7   24.0       L
## 21   B   9.2   24.0       R
## 25   G   8.1   24.2       R
## 29   B   8.9   24.2       R
## 33   G   8.6   24.5       R
## 37   G   9.0   26.0       R
```

