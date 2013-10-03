
```r

## SHAPES

plot(1:2, type = "n", xlim = c(1, 100), ylim = c(1, 100), xlab = "", ylab = "")
angles <- seq(0, 2 * pi, length = 1000)
polygon(50 + 30 * cos(angles), 45 + 30 * sin(angles), col = "#ABC7FF", border = "NA")
polygon(25 + 15 * cos(angles), 65 + 25 * sin(angles), col = "#CC99FF99", border = "NA")
polygon(c(69, 85, 92, 77, 62), c(48, 48, 66, 82, 66), col = "#FFFF0099", border = "NA")
polygon(c(18, 42, 42, 18), c(36, 36, 60, 60), col = "#00CC0099", border = "blue", 
    lwd = 7)
polygon(c(25, 40, 40, 25), c(8, 8, 23, 23), border = "black", lwd = "1", col = "#FF000099")
polygon(c(25, 40, 40, 25), c(8, 8, 23, 23), border = "black", lwd = "1", col = "#FF000050")
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 

