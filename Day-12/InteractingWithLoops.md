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
load("/home/aweberg/NEW-CS121/latencyData.RData")
latencyData
```

```
##      interval latency
## 1    0.100000  0.2295
## 2    2.188333  0.5880
## 3    0.661560  0.9214
## 4    1.784996  0.6195
## 5    0.297880  0.5152
## 6    0.336823  0.5220
## 7    4.469092  0.8852
## 8    0.009973  0.7448
## 9    2.421471  0.9295
## 10   1.709935  0.7160
## 11   0.949664  0.6526
## 12   0.735041  0.9810
## 13   1.835598  0.5251
## 14   0.076301  0.8510
## 15   5.619755  0.8293
## 16   0.970849  0.4895
## 17   0.810853  0.6388
## 18   4.776696  0.9771
## 19   2.388579  0.8095
## 20   2.611932  0.6800
## 21   0.181768  0.6406
## 22   1.697724  0.7273
## 23   3.304539  0.8687
## 24   0.575328  0.5493
## 25   0.619444  0.6156
## 26   3.464911  0.7093
## 27   5.015682  0.6853
## 28   1.632148  0.7536
## 29   0.900992  0.7501
## 30   2.950787  0.7539
## 31   0.663071  0.6569
## 32   8.296597  0.6309
## 33   7.620749  0.6006
## 34   0.814060  0.7967
## 35   4.089351  0.8748
## 36   0.116257  0.6097
## 37   0.616356  0.7499
## 38   1.426504  0.9978
## 39   5.013384  0.7058
## 40   1.420455  0.5535
## 41   1.968183  0.8812
## 42   0.207610  0.5412
## 43   3.206556  0.6230
## 44   3.746948  0.5413
## 45   1.292131  0.9117
## 46   1.021152  0.6037
## 47   1.376326  0.7283
## 48   0.708864  0.8419
## 49   2.490803  0.8059
## 50   2.512580  0.7409
## 51   0.954565  0.8737
## 52   0.760674  0.8162
## 53   2.343641  0.7852
## 54   5.311772  0.8690
## 55   0.448039  0.5460
## 56   0.082681  0.6147
## 57   5.269323  0.8301
## 58   0.409220  1.1934
## 59   1.799767  0.6527
## 60   2.564643  0.7027
## 61   0.341438  0.4452
## 62   1.822898  0.5382
## 63   1.003558  0.7457
## 64   0.671293  0.5481
## 65   1.739543  0.7366
## 66   0.997021  0.6402
## 67   2.494251  0.7572
## 68   0.820434  0.8408
## 69   0.781080  0.4422
## 70   2.755724  0.9835
## 71   1.244041  1.1463
## 72   0.581480  0.6863
## 73   1.181749  0.8033
## 74  10.999794  0.9473
## 75   1.067630  0.9273
## 76   4.815886  0.9568
## 77   3.126830  0.9960
## 78   0.459212  0.6997
## 79   0.391126  0.8988
## 80   1.287184  0.6894
## 81   1.354412  0.7120
## 82   5.476585  0.6571
## 83   3.576985  0.9420
## 84   7.985055  0.6265
## 85   3.164735  0.9814
## 86   0.307527  0.6941
## 87   0.131415  0.5729
## 88   0.680423  0.8543
## 89   0.763387  0.8141
## 90   1.048147  0.5622
## 91   0.238174  0.7635
## 92   1.179137  0.6840
## 93   3.128704  0.6245
## 94   2.091110  0.7034
## 95   3.250093  0.9041
## 96   0.446066  0.7056
## 97   3.555866  0.5824
## 98   7.420200  0.8427
## 99   0.255598  0.5261
## 100  4.388392  0.8793
```

```r
plot(latencyData[[1]], latencyData[[2]], xlab = "Time Interval", ylab = "Response Time", 
    main = "Response Time vs. Time Interval")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

As can be seen, there seems to be some correlation showing that the larger the time interval, the higher the response time.


## Elaboration

```r
testLatency2 <- function(N) {
    result <- vector(length = N)
    wordLength <- round(runif(N, 1, 20))
    for (k in 1:N) {
        x <- sample(letters, wordLength[k])
        word <- paste(x, collapse = "")
        phrase <- paste("Type the word, '", word, "' ", sep = " ")
        command <- readline(phrase)
        Sys.sleep(runif(1, min = 1, max = 5))
        before <- Sys.time()
        while (command != word) {
            command <- readline("Try Again")
        }
        readline("Press Enter:")
        after <- Sys.time()
        delay <- as.numeric(after - before)
        cat(rep("\n", 20))
        result[k] <- delay
    }
    table <- data.frame(`Word Length` = WordLength, Latency = result)
    return(table)
}
```


