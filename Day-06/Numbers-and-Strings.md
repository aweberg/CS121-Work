Numbers and Strings
================

  
## Basic Statistics

```r
outlier <- function(x) {
    q <- quantile(x, probs = c(0.25, 0.75))
    width <- 1.5 * (q[[2]] - q[[1]])
    high <- width + q[[2]]
    low <- q[[1]] - width
    return(x[(x < low) | (x > high)])
}
outlier(c(1, 2, 3, 4, 22))
```

```
## [1] 22
```

```r
outlier(c(75, 76, 77, 78, 77, 77, 73, 76, 1, 300))
```

```
## [1]   1 300
```



```r
outlier <- function(x) {
    q <- quantile(x, probs = c(0.25, 0.75))
    width <- 1.5 * (q[[2]] - q[[1]])
    high <- width + q[[2]]
    low <- q[[1]] - width
    out <- c()
    for (k in 1:length(x)) {
        out <- c(out, x[k] > high | x[k] < low)
    }
    return(out)
}
outlier(c(1, 2, 3, 4, 22))
```

```
## [1] FALSE FALSE FALSE FALSE  TRUE
```

```r
outlier(c(75, 76, 77, 78, 77, 77, 73, 76, 1, 300))
```

```
##  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE
```


## Numbers and Languages

```r
English <- c("zero", "one", "two", "three", "four", "five", "six", "seven", 
    "eight", "nine")
Spanish <- c("cero", "uno", "dos", "tres", "cuatro", "cinco", "seis", "siete", 
    "ocho", "nueve")
digitToWord <- function(n, language) {
    return(language[n + 1])
}
digitToWord(4, English)
```

```
## [1] "four"
```

```r
digitToWord(7, Spanish)
```

```
## [1] "siete"
```


## Help for Crossword Puzzles

```r
lettersMatch <- function(pattern) {
    words <- readLines(url("http://dtkaplan.github.io/ScientificComputing/Syllabus/Daily/Day-07/word_list_moby_crossword-flat/word_list_moby_crossword.flat.txt"))
    analyze <- grepl(pattern, words)
    return(words[analyze])
}
# 7 letter words starting with 'b' ending in 'ing'
lettersMatch("^.t..r..$")
```

```
##  [1] "athirst" "attired" "attires" "attorns" "etheric" "starred" "stearic"
##  [8] "stearin" "steered" "steerer" "stirred" "stirrer" "stirrup" "stoures"
## [15] "stourie" "uttered" "utterer" "utterly"
```

## Have your pi two ways

```r
piSeries <- function(n) {
    state <- 0
    for (k in 1:length(n)) {
        result <- ((-1)^(k + 1))/(2 * k - 1)
        state <- state + result
    }
    return(state * 4)
}
piSeries(1:10000)
```

```
## [1] 3.141
```


