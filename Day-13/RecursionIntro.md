Recursion
==========

## Loop of Fibonacci Numbers
#### Given Example:

```r
fibLoop <- function(n) {
    Ffirst <- 0
    Fsecond <- 1
    for (k in 2:n) {
        newF <- Ffirst + Fsecond
        Ffirst <- Fsecond
        Fsecond <- newF
    }
    return(newF)
}

fibLoop(5)
```

```
## [1] 5
```

```r
fibLoop(20)
```

```
## [1] 6765
```

#### Loop where the state is maintained by a vector of n+1 slots, with the first two slots initialized to 0 and 1 respectively:

```r
fibLoop2 <- function(n) {
    sofar = c(0, 1)
    for (k in 3:n) {
        sofar[k] <- sofar[k - 1] + sofar[k - 2]
        sofar[k + 1] <- sofar[k] + sofar[k - 1]
    }
    return(sofar[k + 1])
}

fibLoop2(5)
```

```
## [1] 5
```

```r
fibLoop2(20)
```

```
## [1] 6765
```

#### Returns all fibonacci numbers n and below:

```r
fibLoop2 <- function(n) {
    sofar = c(0, 1)
    for (k in 3:n) {
        sofar[k] <- sofar[k - 1] + sofar[k - 2]
        sofar[k + 1] <- sofar[k] + sofar[k - 1]
    }
    return(sofar)
}

fibLoop2(5)
```

```
## [1] 0 1 1 2 3 5
```

```r
fibLoop2(20)
```

```
##  [1]    0    1    1    2    3    5    8   13   21   34   55   89  144  233
## [15]  377  610  987 1597 2584 4181 6765
```


## A Recursive structure for Fn
#### Given Example:

```r
fibRecurse <- function(n) {
    if (n == 1) {
        return(1)
    } else {
        if (n == 0) 
            return(0)
    }
    thisF <- fibRecurse(n - 1) + fibRecurse(n - 2)
    return(thisF)
}

fibRecurse(5)
```

```
## [1] 5
```

```r
fibRecurse(20)
```

```
## [1] 6765
```

#### More concise way:

```r
fib1 <- function(n) {
    if (n < 2) 
        return(n)
    return(fib1(n - 1) + fib1(n - 2))
}

fib1(5)
```

```
## [1] 5
```

```r
fib1(20)
```

```
## [1] 6765
```


## Exercises
#### Write a recursive function to add up the numbers from n to zero:

```r
addNSeq <- function(n) {
    if (n == 1) {
        return(1)
    } else {
        if (n == 0) {
            return(0)
        }
    }
    sum <- addNSeq(n - 1) + n
    return(sum)
}

addNSeq(3)
```

```
## [1] 6
```

```r
addNSeq(5)
```

```
## [1] 15
```

#### Looping Version:

```r
addNSeqLoop <- function(n) {
    sum <- 0
    for (k in 1:n) {
        sum <- n - k + sum
    }
    return(sum + n)
}

addNSeqLoop(3)
```

```
## [1] 6
```

```r
addNSeqLoop(5)
```

```
## [1] 15
```

#### Simple vectorized operational version:

```r
addNSeqSimple <- function(n) {
    vect <- 1:n
    return(sum(vect))
}

addNSeqSimple(3)
```

```
## [1] 6
```

```r
addNSeqSimple(5)
```

```
## [1] 15
```

#### Write a recursive function to add up all the numbers in a vector:

```r
addRecursively <- function(v) {
    if (length(v) == 1) {
        return(v[1])
    }
    sum <- addRecursively(v[-length(v)]) + v[length(v)]
    return(sum)
}

addRecursively(c(1, 2, 3))
```

```
## [1] 6
```

```r
addRecursively(c(5, 7, 9))
```

```
## [1] 21
```

#### Loop Version:

```r
addWithLoop <- function(v) {
    sum <- 0
    for (k in 1:length(v)) {
        sum <- v[k] + sum
    }
    return(sum)
}

addWithLoop(c(1, 2, 3))
```

```
## [1] 6
```

```r
addWithLoop(c(5, 7, 9))
```

```
## [1] 21
```

#### Simple vectorized operational version:

```r
addSimple <- function(v) {
    sum(v)
}

addSimple(c(1, 2, 3))
```

```
## [1] 6
```

```r
addSimple(c(5, 7, 9))
```

```
## [1] 21
```




