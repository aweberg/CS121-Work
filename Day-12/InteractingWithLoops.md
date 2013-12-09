Side Effects and Inputs
=======================

## Looping a Launch

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


## Testing Human Response Times

```r
responseTime <- function(N) {
    readline("PRESS RETURN WHEN READY:")
    result <- rep(NA, N)
    interval <- c(0.1)
    for (k in 1:N) {
        before <- Sys.time()
        readline("PRESS RETURN:")
        after <- Sys.time()
        delay <- as.numeric(after - before)
        cat(rep("\n", 20))
        result[k] <- delay
        a <- Sys.time()
        Sys.sleep(rexp(20, rate = 1/2))
        b <- Sys.time()
        c <- as.numeric(b - a)
        interval <- c(interval, c)
    }
    latency <- result[1:N]
    finish <- data.frame(interval = interval[1:N], latency = latency)
    return(finish)
}
```



```r

latencyData <- load("latencyData.RData")
```

```
## Warning: cannot open compressed file 'latencyData.RData', probable reason
## 'No such file or directory'
```

```
## Error: cannot open the connection
```

```r
plot(latencyData[[1]], latencyData[[2]], xlab = "Time Interval", ylab = "Response Time")
```

```
## Error: object 'latencyData' not found
```


## Elaboration

```r
testLatency <- function(N) {
  readline("Press Enter when you are ready:")
  result <- rep(0, N)
  for( k in 1:N) {
    Sys.sleep(runif(1,min=1,max=5))
    before <- Sys.time()
    readline("Press Enter:")
    after <- Sys.time()
  delay <- as.numeric(after-before)
    cat(rep("\n",20))
    result[k] <- delay
 
    }
  return(result)
}

(I still need to add list of words)

SPF <- testLatency(20)
  while(readline != #one word){
          oneword <- a random choice of another word
          print out, "Sorry, try again"
  }

```
