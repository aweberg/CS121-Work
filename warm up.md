10/8
=======


```r
mySum <- function(v) {
    sofar <- 0
    k <- 1
    repeat {
        sofar <- sofar + v[k]
        k <- k + 1
        if (k == length(v) + 1) 
            break
    }
    return(sofar)
}
```

Test Statements:

```r
mySum(1:3)
```

```
## [1] 6
```

```r

mySum(c(4, 6, 1))
```

```
## [1] 11
```



```r

mySumWhile <- function(v) {
    sofar <- 0
    k <- 1
    while (k != length(v) + 1) {
        sofar <- sofar + v[k]
        k <- k + 1
    }
    return(sofar)
}
```

Test Statements:

```r
mySumWhile(1:3)
```

```
## [1] 6
```

```r

mySumWhile(c(4, 6, 1))
```

```
## [1] 11
```



```r

mySumFor <- function(v) {
    sofar <- 0
    for (k in 1:length(v)) {
        sofar <- sofar + v[k]
    }
    return(sofar)
}
```

Test Statements:

```r
mySumFor(1:3)
```

```
## [1] 6
```

```r

mySumFor(c(4, 6, 1))
```

```
## [1] 11
```



```r

myRunningSum <- function(v) {
    alpha <- 0
    beta <- c()
    for (k in v) {
        alpha <- alpha + k
        beta <- c(beta, alpha)
    }
    return(beta)
}
```

Test Statements:

```r
myRunningSum(1:4)
```

```
## [1]  1  3  6 10
```

            

```r
myRevRunSum <- function(v) {
    alpha <- 0
    beta <- c()
    for (k in v) {
        alpha <- alpha + k
        beta <- c(alpha, beta)
    }
    return(beta)
}
```

Test Statements:

```r
myRevRunSum(1:4)
```

```
## [1] 10  6  3  1
```



```r

myUnique <- function(v) {
    alpha <- c()
    for (k in v) {
        if (!(k %in% alpha)) 
            alpha <- c(alpha, k)
    }
    return(alpha)
}

myUnique(c(1, 1, 2, 3))
```

```
## [1] 1 2 3
```

