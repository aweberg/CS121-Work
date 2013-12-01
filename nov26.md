Nov 26
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
require(reshape2)
```

```
## Loading required package: reshape2
```

```r
grades <- fetchData("grades.csv")
```

```
## Retrieving from http://www.mosaic-web.org/go/datasets/grades.csv
```



```r
both <- join(grades, grade2)
```

```
## Error: object 'grade2' not found
```

```r
head(both)
```

```
## Error: object 'both' not found
```





