October 15
===========


```r
x <- 99
f <- function(x) {
    x <- 2 * x
    return(x)
}

f(4)
```

```
## [1] 8
```

```r

f <- function() {
    x <- 2 * x
    return(x)
}

f()
```

```
## [1] 198
```



```r
f <- function() {
    x <<- 2 * x
    return(x)
}

f()
```

```
## [1] 198
```

```r
f(4)
```

```
## Error: unused argument (4)
```

```r
f(x)
```

```
## Error: unused argument (x)
```

```r
x
```

```
## [1] 198
```

```r

f <- function(x) {
    x <<- 2 * x
    return(x)
}

f(4)
```

```
## [1] 4
```

```r
x
```

```
## [1] 8
```



```r
y <- "hello"
assign("y", "hello", globalenv())

ls(globalenv())
```

```
## [1] "f" "x" "y"
```

```r

get("y", globalenv())
```

```
## [1] "hello"
```

```r
with(globalenv(), y)
```

```
## [1] "hello"
```





```r

addEm <- function(v) {
    alpha <- 0
    for (k in 1:length(v)) {
        alpha <- alpha + v[k]
    }
    return(alpha)
}

addEm(c(5, 3, 1))
```

```
## [1] 9
```



```r
newaddEm <- function(v) {
    if (length(v) == 0) 
        return(0)
    return(v[1] + newaddEm(v[-1]))
}

newaddEm(1:3)
```

```
## [1] 6
```


