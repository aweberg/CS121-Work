Numbers and Strings
================


```r
giveoutliers <- function(v) {
    a <- quantile(v)
    b <- a[[2]]
    c <- a[[4]]
    x <- v[which(v > c)]
    y <- v[which(v < b)]
    return(c(y, x))
}

giveoutliers(c(1, 2, 3, 4, 22))
```

```
## [1]  1 22
```




