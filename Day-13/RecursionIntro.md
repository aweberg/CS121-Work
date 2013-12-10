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


## Natural Settings for Recursion

```r
simpleRiemann <- function(f, a = 0, b = 1, n = 3) {
    rectangleWidth = (b - a)/n
    midpoints <- seq(a + rectangleWidth/2, b - rectangleWidth/2, length = n)
    rectangleAreas <- sapply(midpoints, f) * rectangleWidth
    return(sum(rectangleAreas))
}
```



```r
integrateRiemann <- function(f, a = 0, b = 1) {
    nbins <- 5
    biggerBins <- simpleRiemann(f, a = a, b = b, n = nbins)
    for (k in 1:5) {
        nbins <- nbins * 10  # much smaller bins
        smallerBins <- simpleRiemann(f, a = a, b = b, n = nbins)
        if (abs(smallerBins - biggerBins) < 1e-05) 
            break
        biggerBins <- smallerBins
    }
    return(smallerBins)
}
```

Demo Cases:

```r
integrateRiemann(function(x) {
    3 * x
}, a = 0, b = 10)
```

```
## [1] 150
```



```r
integrateRiemann(function(x) {
    3 * x^2
}, a = 0, b = 10)
```

```
## [1] 1000
```



#### Why is there a for() loop only going to 5?
Because each time we go through the loop the number of bins in multiplied by 10, by using k in 1:5, we are effectively increasing the number of bins by 10^5

#### What's the purpose of biggerBins <- smallerBins?
Setting biggerBins <- smallerBins makes the biggerBins smaller and smaller each time it goes through the loop.  This is what makes the recursion possible.

#### In the worst case, how many bins will there be?
In the worst case, there will be 5*10^5 bins.

## Your Tasks
#### Modify integrateRecursive()

```r
integrateRecursive <- function(f, a = 0, b = 1) {
    bigBins <- simpleRiemann(f, a = a, b = b, n = 5)
    smallBins <- simpleRiemann(f, a = a, b = b, n = 10)
    if (abs(bigBins - smallBins) < 1e-05) 
        return(smallBins) else {
        mid <- (a + b)/2
        total <- integrateRecursive(f, a = a, b = mid) + integrateRecursive(f, 
            a = mid, b = b)
        if (n == 10000) {
            break
        }
        return(total)
    }
}
```


#### Demo your Program

```r
integrateRecursive(function(x) {
    3 * x
}, a = 0, b = 10)
```

```
## [1] 150
```

$\int\limits_{0}^{10} 3*x dx = 150$


```r
integrateRiemann(function(x) {
    x^2
}, a = 0, b = 10)
```

```
## [1] 333.3
```

$\int\limits_{0}^{10} 3*x^2 dx = \frac{1000}{3}$

Integral that hits "worst case":

```r
integrateRiemann(function(x) {
    x^309
}, a = 0, b = 10)
```

```
## Error: missing value where TRUE/FALSE needed
```

$\int\limits_{0}^{10} x^{309} dx = 3.23*10^{307}$

#### A Better Simple Integrator

```r
gaussQuadrature <- function(f, a = 0, b = 1) {
    # Just 4 function evaluations!
    
    # 'Magic' values on z in [0,1]
    z <- c(c(-1, 1) * sqrt((3 - 2 * sqrt(6/5))/7), c(-1, 1) * sqrt((3 + 2 * 
        sqrt(6/5))/7))
    # weights (analogous to bin width)
    w <- c(rep((18 + sqrt(30))/36, 2), rep((18 - sqrt(30))/36, 2))
    # Translate to interval x in [a,b]
    x <- ((b - a)/2) * z + (a + b)/2
    # evaluate the function at x, multiply by weights, and sum
    return(((b - a)/2) * sum(w * sapply(x, f)))
}
```

Test Cases:

```r
gaussQuadrature(function(x) 3 + 0 * x, 0, 10)
```

```
## [1] 30
```

```r
gaussQuadrature(function(x) 3 * x, 0, 10)
```

```
## [1] 150
```

```r
gaussQuadrature(function(x) 3 * x^2, 0, 10)
```

```
## [1] 1000
```


#### What power of x does gaussQuadrature fail for? ---> 318

```r
gaussQuadrature(function(x) x^317, 0, 10)
```

```
## [1] 2.155e+307
```

```r
gaussQuadrature(function(x) x^318, 0, 10)
```

```
## [1] Inf
```


#### Test out gaussQuadrature() on sine and cosine functions, with a=0 and b successively larger, that is, b=0.1, b=1.0, and so on. How wide can you make the interval, before the result of gaussQuadrature() is not accurate? ---> $2*pi+0.1$

```r
gaussQuadrature(function(x) sin(x), 0, 2 * pi + 0.1)
```

```
## [1] 0.005379
```

$\int\limits_{0}^{2*pi+0.1}\sin{x}dx = 0.004995$

#### Re-implement integrateRecursive() using gaussQuadrature() as the base integrator. You'll have to be creative, since you can't change the number of bins as in the test-for-simple part of integrateRecursive(). Show that your function works on trigonometric functions with b big.

```r
integrateRecursive2 <- function(f, a = 0, b = 1) {
    bigBins <- gaussQuadrature(f, a = a, b = b, n = 5)
    smallBins <- gaussQuadrature(f, a = a, b = b, n = 10)
    if (abs(bigBins - smallBins) < 1e-05) 
        return(smallBins) else {
        mid <- (a + b)/2
        total <- integrateRecursive2(f, a = a, b = mid) + integrateRecursive2(f, 
            a = mid, b = b)
        if (n == 10000) {
            break
        }
        return(total)
    }
}
```


### Plotting a function

```r

plotF <- function(f, a = 0, b = 1) {
    diff <- (b - a)
    x <- seq(a, b, length = (diff * 100))
    y <- f(x)
    plot(x, y, xlab = "x", ylab = "f(x)", main = "plotF", type = "l", pch = 20, 
        cex = 0.2, col = "red")
}

plotF(function(x) x^3, -1, 1)
```

![plot of chunk unnamed-chunk-25](figure/unnamed-chunk-25.png) 






