October 17
=============

# Reverse a vector, recursively


```r
revrec <- function(v) {
    if (length(v) == 1) 
        return(v) else {
        c(revrec(v[-1]), v[1])
    }
}

revrec(c(5, 4, 3, 2, 1))
```

```
## [1] 1 2 3 4 5
```

