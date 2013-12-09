Computing Numerical Derivatives
======================

Task I 

```r
f <- function(x) {
    exp(-x/3) * cos(x)
}

Df <- D(exp(-x/3) * cos(x) ~ x)
```

```
## Error: argument "name" is missing, with no default
```

```r

evalD <- function(f, x) {
    h <- 1e-08  # 'Small h'
    return((f(x + h) - f(x - h))/(2 * h))
}

i <- function(x) {
    evalD(f, x)
}
j <- function(x) {
    Df(x)
}
plotFun(i(x) ~ x, x.lim = range(-1e-08, 1e-08), col = "red")
```

```
## Error: could not find function "plotFun"
```

```r
plotFun(j(x) ~ x, x.lim = range(-1e-08, 1e-08), col = "blue", add = TRUE)
```

```
## Error: could not find function "plotFun"
```

```r

plotFun(i(x) - j(x) ~ x, add = FALSE, x.lim = range(-1e-08, 1e-08), col = "blue")
```

```
## Error: could not find function "plotFun"
```

Task II 


```r
evalD <- function(f, x) {
    h <- 1e-08  # 'Small h'
    return((f(x + h) - f(x - h))/(2 * h))
}

evalD <- function(f, x, h = 1e-08) {
    return((f(x + h) - f(x - h))/(2 * h))
}
```

