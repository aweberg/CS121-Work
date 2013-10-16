October 10
==========

## Base Conversion

```r

baseToNumeric <- function(N, b) {
    howMany <- length(N)
    herdsize <- b^((howMany - 1):0)
    return(sum(as.numeric(N) * herdsize))
}

baseToNumeric(c("7", "6", "5", "4"), 8)
```

```
## [1] 4012
```


## As a Loop:

```r

convertAsALoop <- function(N, b) {
    N <- as.numeric(N)
    sheepcount <- 0
    boxsize <- 1
    for (k in (length(N):1)) {
        sheepcount <- sheepcount + boxsize * N[k]
        boxsize <- boxsize * b
    }
    return(sheepcount)
}

convertAsALoop(c("7", "6", "5", "4"), 8)
```

```
## [1] 4012
```


## Blastoff

```r

blastoff <- function(x) {
    while (x != 0) {
        Sys.sleep(1)
        cat(x, "\n")
        x <- x - 1
    }
    Sys.sleep(1)
    cat("BANANAS!!!")
}

blastoff(5)
```

```
## 5 
## 4 
## 3 
## 2 
## 1 
## BANANAS!!!
```

