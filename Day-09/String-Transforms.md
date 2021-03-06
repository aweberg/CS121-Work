String Transformations
========

## Reverser

```r
reverser <- function(x) {
    return(rev(strsplit(x, split = character(0))[[1]][1:nchar(x)]))
}

reverser <- function(x) {
    a <- strsplit(x, split = character(0))[[1]]
    b <- a[rev(1:nchar(x))]
    paste(b, collapse = "")
}
```


Test Statements:

```r
reverser("hello")
```

```
## [1] "olleh"
```


## Scrambler

```r
scrambleword <- function(x) {
    a <- strsplit(x, split = character(0))[[1]]
    b <- a[sample(1:nchar(x))]
    paste(b, collapse = "")
}
```

Test Statements:

```r
scrambleword("hello")
```

```
## [1] "hleol"
```


## VowelBleeper

```r
vowelbleep <- function(x) {
    a <- gsub("[aeiou]", "*", (strsplit(x, split = "")[[1]][1:nchar(x)]))
    b <- paste(a, collapse = "")
    return(b)
}
```

Test Statements:

```r
vowelbleep("hello")
```

```
## [1] "h*ll*"
```


## L33t


```r
L33t <- function(x) {
    a <- gsub("l", "1", x)
    b <- gsub("z", "2", a)
    c <- gsub("e", "3", b)
    d <- gsub("x", "4", c)
    e <- gsub("s", "5", d)
    f <- gsub("t", "7", e)
    g <- gsub("b", "8", f)
    h <- gsub("g", "9", g)
    i <- gsub("o", "0", h)
    return(i)
}

L33t("abcdefghijklmnopqrstuvwxyz")
```

```
## [1] "a8cd3f9hijk1mn0pqr57uvw4y2"
```

```r
L33t(c("alex is the best"))
```

```
## [1] "a134 i5 7h3 8357"
```

