Base Conversion
=====


```r

toBase <- function(z, b) {
    alpha <- c()
    while (z > 0) {
        r <- z%%b
        alpha <- c(alpha, r)
        z <- (z - r)/b
    }
    return(alpha)
}

toBase(20, 3)
```

```
## [1] 2 0 2
```

