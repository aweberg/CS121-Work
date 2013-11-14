Crossword
===========

```r
words <- readLines(url("http://dtkaplan.github.io/ScientificComputing/Syllabus/Daily/Day-07/word_list_moby_crossword-flat/word_list_moby_crossword.flat.txt"))

v1 <- words[grepl("^.$", words) == TRUE]
length(v1)
```

```
## [1] 0
```


```r
v2 <- words[grepl("^..$", words) == TRUE]
length(v2)
```

```
## [1] 85
```


```r
v3 <- words[grepl("^...$", words) == TRUE]
length(v3)
```

```
## [1] 908
```


```r
v4 <- words[grepl("^....$", words) == TRUE]
length(v4)
```

```
## [1] 3686
```


```r
v5 <- words[grepl("^.....$", words) == TRUE]
length(v5)
```

```
## [1] 8258
```


```r
v6 <- words[grepl("^......$", words) == TRUE]
length(v6)
```

```
## [1] 14374
```

```r

v7 <- words[grepl("^.......$", words) == TRUE]
length(v7)
```

```
## [1] 21727
```

```r

v8 <- words[grepl("^........$", words) == TRUE]
length(v8)
```

```
## [1] 26447
```

```r

v9 <- words[grepl("^.........$", words) == TRUE]
length(v9)
```

```
## [1] 16658
```

```r

v10 <- words[grepl("^..........$", words) == TRUE]
length(v10)
```

```
## [1] 9199
```

```r

v11 <- words[grepl("^...........$", words) == TRUE]
length(v11)
```

```
## [1] 5296
```

```r

v12 <- words[grepl("^............$", words) == TRUE]
length(v12)
```

```
## [1] 3166
```

```r

v13 <- words[grepl("^.............$", words) == TRUE]
length(v13)
```

```
## [1] 1960
```

```r

v14 <- words[grepl("^..............$", words) == TRUE]
length(v14)
```

```
## [1] 1023
```

```r

v15 <- words[grepl("^...............$", words) == TRUE]
length(v15)
```

```
## [1] 557
```

```r

v16 <- words[grepl("^................$", words) == TRUE]
length(v16)
```

```
## [1] 261
```

```r

v17 <- words[grepl("^.................$", words) == TRUE]
length(v17)
```

```
## [1] 132
```

```r

v18 <- words[grepl("^..................$", words) == TRUE]
length(v18)
```

```
## [1] 48
```

```r

v19 <- words[grepl("^...................$", words) == TRUE]
length(v19)
```

```
## [1] 16
```

```r

v20 <- words[grepl("^....................$", words) == TRUE]
length(v20)
```

```
## [1] 5
```

```r

v21 <- words[grepl("^.....................$", words) == TRUE]
length(v21)
```

```
## [1] 3
```

```r

v22 <- words[grepl("^......................$", words) == TRUE]
length(v22)
```

```
## [1] 0
```




```r

wordLength<-function(x){
  list<-c()
  for(k in 1:length(words)){
    a<-strsplit(words[k],"")
    b<-a[[1]]
    c<-length(b)==x
    list<-c(list,c)}
  d<-which(list==TRUE)
  return(length(d))
  }

wordLength(2)

wordLength2 <- function(x){
  if x==1{v=""}|
  if x==2{v="."} 
  list<-c("")
```

v20<-words[grepl("^....................$",words)==TRUE]
length(v20)
