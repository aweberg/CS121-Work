Day 10
========
### Factorial

```r
myfactorial <- function(n) {
    res <- 1
    for (k in 1:n) {
        res <- res * k
    }
    return(res)
}

myfactorial(4)
```

```
## [1] 24
```

    
### Sum factorial

```r
mysum <- function(n) {
    res <- 0
    for (k in 1:n) {
        res <- res + k
    }
    return(res)
}

mysum(3)
```

```
## [1] 6
```


### Scrabble finder

```r
words <- readLines(url("http://dtkaplan.github.io/ScientificComputing/Syllabus/Daily/Day-07/word_list_moby_crossword-flat/word_list_moby_crossword.flat.txt"))

findscrabble <- function(letters) {
    words <- words[grep(letters[1], words)]
    words <- words[grep(letters[2], words)]
    words <- words[grep(letters[3], words)]
    return(words)
}
length(findscrabble(c("b", "n", "r")))
```

```
## [1] 2304
```



```r
findscrabble2 <- function(letters) {
    for (k in 1:length(letters)) {
        words <- words[grep(letters[k], words)]
    }
    return(words)
}

length(findscrabble2(c("b", "n", "r", "h")))
```

```
## [1] 234
```



```r
findscrabble3 <- function(letters) {
    for (k in 1:length(letters)) {
        words <- words[grep(letters[k], words)]
        if (length(words) < 10) 
            break
    }
    return(words)
}

findscrabble3(c("b", "n", "r", "x", "a", "c", "z"))
```

```
## [1] "exacerbating" "exuberance"   "exuberances"  "inextricable"
## [5] "inextricably"
```

```r
## No z in any of these words, however they have b,n,r,x,a,c
```


### Fibanacci Numbers

```r
fib <- function(n) {
    current <- 1
    beforeIt <- 0
    for (k in 1:n) {
        tmp <- current + beforeIt
        beforeIt <- current
        current <- tmp
    }
    return(current)
}

fib(1)
```

```
## [1] 1
```

```r
fib(6)
```

```
## [1] 13
```



```r
fib2 <- function(n) {
    sofar = c(0, 1)
    for (k in 3:n) {
        sofar[k] <- sofar[k - 1] + sofar[k - 2]
    }
    return(sofar)
}

fib2(8)
```

```
## [1]  0  1  1  2  3  5  8 13
```

```r
fib2(20)
```

```
##  [1]    0    1    1    2    3    5    8   13   21   34   55   89  144  233
## [15]  377  610  987 1597 2584 4181
```

  

```r

fib3 <- function(n) {
    if (n < 0 | round(n) != n) {
        warning("YOUR n SUCKS YO")
        return(NA)
    }
    sofar = c(0, 1)
    for (k in 3:n) {
        sofar[k] <- sofar[k - 1] + sofar[k - 2]
    }
    return(sofar)
}

fib3(4)
```

```
## [1] 0 1 1 2
```

```r
fib3(-1)
```

```
## Warning: YOUR n SUCKS YO
```

```
## [1] NA
```

```r
fib3(3.7)
```

```
## Warning: YOUR n SUCKS YO
```

```
## [1] NA
```


### Prime Numbers

```r
primesieve <- function(n) {
    guess <- rep(TRUE, n)
    inds <- 1:n
    for (k in 2:100) {
        if (guess[k]) {
            guess[inds%%k == 0 & inds > k] <- FALSE
        }
    }
    return(which(guess))
}

primesieve(3)
```

```
## Error: missing value where TRUE/FALSE needed
```

```r
primesieve(100)
```

```
##  [1]  1  2  3  5  7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79
## [24] 83 89 97
```

          
