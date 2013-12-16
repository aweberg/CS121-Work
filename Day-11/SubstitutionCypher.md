Substitution Cypher
===================


## Key

```r
key <- "zoo"
TheKey <- function(L) {
    which(L == letters)
}
paste(sapply(unlist(strsplit(key, split = NULL)), FUN = TheKey), collapse = "")
```

```
## [1] "261515"
```


## Cypher

```r
set.seed(paste(sapply(unlist(strsplit(key, split = NULL)), FUN = TheKey), collapse = ""))
characters <- c(letters, LETTERS, ".", ":", ",", ";", 0:9)
fromandto <- sample(characters)
fromandto
```

```
##  [1] "q" "z" "j" ":" "D" "s" "i" "F" "y" "a" "8" "W" "K" "O" "f" "k" "d"
## [18] "u" "L" "," "P" "l" "Q" "E" "C" "Z" "A" "n" "G" "X" "g" "o" "b" "S"
## [35] "J" "m" "V" "v" "7" "H" "e" "Y" "6" "4" "5" "0" "2" "U" "1" "r" "t"
## [52] "w" "h" ";" "p" "M" "9" "x" "3" "I" "R" "c" "T" "." "B" "N"
```


## Encryption

```r
CBCoutput <- chartr(paste(characters, collapse = ""), paste(fromandto, collapse = ""), 
    "Messsage Encrypted")
CBCoutput
```

```
## [1] "7DLLLqiD gOjuCk,D:"
```


## Decryption

```r
decoded <- chartr(paste(fromandto, collapse = ""), paste(characters, collapse = ""), 
    CBCoutput)
decoded
```

```
## [1] "Messsage Encrypted"
```


## Mystery Novel
(Or whatever literature I happened to have on me)

```r
paragraph <- chartr(paste(characters, collapse = ""), paste(fromandto, collapse = ""), 
    "Production of sodium: The sodium ore is halite (largely NaCl), which is obtained either by evaporation of concentrated salt solutions called brines (see photo) or by mining vast salt deposits formed from the evaporation of prehistoric seas.The Cheshire salt field in Britain, for example, is 60 km by 24 km by 400 m thick and contains more than 90 percent NaCl. Other large deposits occur in New Mexico, Michigan, New York, and Kansas.")
paragraph
```

```
## [1] "Yuf:Pj,yfO fs Lf:yPK; 0FD Lf:yPK fuD yL FqWy,D (WquiDWC HqGW)p QFyjF yL fz,qyOD: Dy,FDu zC Dlqkfuq,yfO fs jfOjDO,uq,D: LqW, LfWP,yfOL jqWWD: zuyODL (LDD kFf,f) fu zC KyOyOi lqL, LqW, :DkfLy,L sfuKD: sufK ,FD Dlqkfuq,yfO fs kuDFyL,fuyj LDqLh0FD GFDLFyuD LqW, syDW: yO nuy,qyOp sfu DEqKkWDp yL T9 8K zC 3R 8K zC R99 K ,Fyj8 qO: jfO,qyOL KfuD ,FqO N9 kDujDO, HqGWh e,FDu WquiD :DkfLy,L fjjPu yO HDQ 7DEyjfp 7yjFyiqOp HDQ tfu8p qO: VqOLqLh"
```

```r

decoded <- chartr(paste(fromandto, collapse = ""), paste(characters, collapse = ""), 
    paragraph)
decoded
```

```
## [1] "Production of sodium: The sodium ore is halite (largely NaCl), which is obtained either by evaporation of concentrated salt solutions called brines (see photo) or by mining vast salt deposits formed from the evaporation of prehistoric seas.The Cheshire salt field in Britain, for example, is 60 km by 24 km by 400 m thick and contains more than 90 percent NaCl. Other large deposits occur in New Mexico, Michigan, New York, and Kansas."
```
