Crosswords-and-Scrabble
======================


```r
words <- readLines(url("http://dtkaplan.github.io/ScientificComputing/Syllabus/Daily/Day-07/word_list_moby_crossword-flat/word_list_moby_crossword.flat.txt"))
```

## Summarizing the List
#### Report of Word Lengths
(Slow version)

```r
wordLength <- function(x) {
    list <- c()
    a <- sapply(words, nchar)
    for (k in 1:length(words)) {
        list <- c(list, a[[k]] == x)
    }
    return(sum(list))
}
wordLength(3)
```

(Fast version)  

```r
wordLength <- function(x) {
    list <- c()
    a <- sapply(words, nchar)
    for (k in 1:length(words)) {
        if (a[[k]] == x) {
            list <- c(list, a[[k]])
        } else {
        }
    }
    return(length(list))
}
```


```r
## 1
wordLength(1)
```

```
## [1] 0
```

```r
## 2
wordLength(2)
```

```
## [1] 85
```

```r
## 3
wordLength(3)
```

```
## [1] 908
```

```r
## 4
wordLength(4)
```

```
## [1] 3686
```

```r
## 5
wordLength(5)
```

```
## [1] 8258
```

```r
## 6
wordLength(6)
```

```
## [1] 14374
```

```r
## 7
wordLength(7)
```

```
## [1] 21727
```

```r
## 8
wordLength(8)
```

```
## [1] 26447
```

```r
## 9
wordLength(9)
```

```
## [1] 16658
```

```r
## 10
wordLength(10)
```

```
## [1] 9199
```

```r
## 11
wordLength(11)
```

```
## [1] 5296
```

```r
## 12
wordLength(12)
```

```
## [1] 3166
```

```r
## 13
wordLength(13)
```

```
## [1] 1960
```

```r
## 14
wordLength(14)
```

```
## [1] 1023
```

```r
## 15
wordLength(15)
```

```
## [1] 557
```

```r
## 16
wordLength(16)
```

```
## [1] 261
```

```r
## 17
wordLength(17)
```

```
## [1] 132
```

```r
## 18
wordLength(18)
```

```
## [1] 48
```

```r
## 19
wordLength(19)
```

```
## [1] 16
```

```r
## 20
wordLength(20)
```

```
## [1] 5
```

```r
## 21
wordLength(21)
```

```
## [1] 3
```

```r
## 22
wordLength(22)
```

```
## [1] 0
```


#### 100 Longest Words
Unfortunately, there are not 100 longest words.  There are 204 of length 17 and above, or else 72 of 18 and above.

```r
wordList <- function(x) {
    list <- c()
    a <- sapply(words, nchar)
    for (k in 1:length(words)) {
        if (a[[k]] == x) {
            list <- c(list, words[k])
        } else {
        }
    }
    return(list)
}
hunWords <- c(wordList(21), wordList(20), wordList(19), wordList(18), wordList(17))
```


```r
length(hunWords)
```

```
## [1] 204
```

```r
hunWords
```

```
##   [1] "counterdemonstrations" "hyperaggressivenesses"
##   [3] "microminiaturizations" "counterdemonstration" 
##   [5] "counterdemonstrators"  "hypersensitivenesses" 
##   [7] "microminiaturization"  "representativenesses" 
##   [9] "anticonservationist"   "comprehensivenesses"  
##  [11] "counterdemonstrator"   "counterinflationary"  
##  [13] "counterpropagations"   "counterretaliations"  
##  [15] "disinterestednesses"   "electrocardiographs"  
##  [17] "extraconstitutional"   "hyperaggressiveness"  
##  [19] "inappropriatenesses"   "inconsideratenesses"  
##  [21] "interdenominational"   "irreconcilabilities"  
##  [23] "miscellaneousnesses"   "multidenominational"  
##  [25] "absentmindednesses"    "adventitiousnesses"   
##  [27] "antiadministration"    "antidiscrimination"   
##  [29] "apprehensivenesses"    "biodegradabilities"   
##  [31] "bloodthirstinesses"    "cantankerousnesses"   
##  [33] "characteristically"    "chemotherapeutical"   
##  [35] "counteraccusations"    "counteraggressions"   
##  [37] "counterpropagation"    "counterretaliation"   
##  [39] "counterrevolutions"    "countersuggestions"   
##  [41] "electrocardiograms"    "electrocardiograph"   
##  [43] "feeblemindednesses"    "heterogenousnesses"   
##  [45] "hydroelectricities"    "hyperconscientious"   
##  [47] "hypernationalistic"    "hypersensitiveness"   
##  [49] "hypersensitivities"    "indispensabilities"   
##  [51] "industrializations"    "interinstitutional"   
##  [53] "internationalizing"    "interrelatednesses"   
##  [55] "irresponsibilities"    "lightheartednesses"   
##  [57] "misinterpretations"    "misrepresentations"   
##  [59] "nondiscriminations"    "obstreperousnesses"   
##  [61] "perpendicularities"    "postfertilizations"   
##  [63] "rehospitalizations"    "remunerativenesses"   
##  [65] "representativeness"    "simultaneousnesses"   
##  [67] "straightforwardest"    "subclassifications"   
##  [69] "subconsciousnesses"    "superintellectuals"   
##  [71] "superintelligences"    "unscrupulousnesses"   
##  [73] "acquaintanceships"     "antiauthoritarian"    
##  [75] "antieavesdropping"     "antiestablishment"    
##  [77] "antimaterialistic"     "antimiscegenation"    
##  [79] "antirevolutionary"     "antitechnological"    
##  [81] "blameworthinesses"     "carnivorousnesses"    
##  [83] "characterizations"     "circumnavigations"    
##  [85] "comprehensiveness"     "consideratenesses"    
##  [87] "constitutionality"     "coproprietorships"    
##  [89] "counteraccusation"     "counteraggression"    
##  [91] "counterchallenges"     "countercomplaints"    
##  [93] "countercriticisms"     "counterinfluences"    
##  [95] "counterrevolution"     "counterstrategies"    
##  [97] "countersuggestion"     "countertendencies"    
##  [99] "counterterrorisms"     "counterterrorists"    
## [101] "cyclophosphamides"     "destructibilities"    
## [103] "disfranchisements"     "disinterestedness"    
## [105] "disqualifications"     "distinctivenesses"    
## [107] "electrocardiogram"     "electromagnetally"    
## [109] "environmentalists"     "extradepartmental"    
## [111] "extragovernmental"     "foresightednesses"    
## [113] "halfheartednesses"     "hardheartednesses"    
## [115] "histopathological"     "homogeneousnesses"    
## [117] "housewifelinesses"     "hydroelectrically"    
## [119] "illustriousnesses"     "impecuniousnesses"    
## [121] "impenetrabilities"     "inaccessibilities"    
## [123] "inappropriateness"     "inattentivenesses"    
## [125] "inconsequentially"     "inconsiderateness"    
## [127] "incorrigibilities"     "indistinguishable"    
## [129] "industrialization"     "industriousnesses"    
## [131] "ineffectivenesses"     "ineffectualnesses"    
## [133] "injudiciousnesses"     "inquisitivenesses"    
## [135] "instrumentalities"     "intelligibilities"    
## [137] "intemperatenesses"     "interdepartmental"    
## [139] "intergovernmental"     "internationalisms"    
## [141] "internationalized"     "internationalizes"    
## [143] "interrelationship"     "irreconcilability"    
## [145] "kaleidoscopically"     "magnanimousnesses"    
## [147] "maintainabilities"     "maneuverabilities"    
## [149] "mellifluousnesses"     "meritoriousnesses"    
## [151] "microminiaturized"     "misappropriations"    
## [153] "miscellaneousness"     "mischievousnesses"    
## [155] "misinterpretation"     "mispronunciations"    
## [157] "misrepresentation"     "mistrustfulnesses"    
## [159] "misunderstandings"     "multidisciplinary"    
## [161] "myelosuppressions"     "nearsightednesses"    
## [163] "nondenominational"     "nondiscrimination"    
## [165] "nondiscriminatory"     "nonindustrialized"    
## [167] "nonproliferations"     "nonrepresentative"    
## [169] "overconscientious"     "overexaggerations"    
## [171] "paleoclimatologic"     "photoelectrically"    
## [173] "photosynthesizing"     "picturesquenesses"    
## [175] "plenipotentiaries"     "postbaccalaureate"    
## [177] "postfertilization"     "postrevolutionary"    
## [179] "precipitatenesses"     "prestidigitations"    
## [181] "pretentiousnesses"     "professionalizing"    
## [183] "programmabilities"     "promiscuousnesses"    
## [185] "reclassifications"     "rehospitalization"    
## [187] "repetitiousnesses"     "reproachfulnesses"    
## [189] "resourcefulnesses"     "responsiblenesses"    
## [191] "straightforwarder"     "subclassification"    
## [193] "superefficiencies"     "superenthusiastic"    
## [195] "superintellectual"     "superintelligence"    
## [197] "superintendencies"     "thoughtlessnesses"    
## [199] "trustworthinesses"     "unconsciousnesses"    
## [201] "underhandednesses"     "undernourishments"    
## [203] "venturesomenesses"     "wrongheadednesses"
```


#### Number of Words Beginning with Each Letter

```r
## A
length(words[grepl("^a", words) == TRUE])
```

```
## [1] 6557
```

```r
## B
length(words[grepl("^b", words) == TRUE])
```

```
## [1] 6848
```

```r
## C
length(words[grepl("^c", words) == TRUE])
```

```
## [1] 10385
```

```r
## D
length(words[grepl("^d", words) == TRUE])
```

```
## [1] 6436
```

```r
## E
length(words[grepl("^e", words) == TRUE])
```

```
## [1] 4364
```

```r
## F
length(words[grepl("^f", words) == TRUE])
```

```
## [1] 4937
```

```r
## G
length(words[grepl("^g", words) == TRUE])
```

```
## [1] 3950
```

```r
## H
length(words[grepl("^h", words) == TRUE])
```

```
## [1] 4080
```

```r
## I
length(words[grepl("^i", words) == TRUE])
```

```
## [1] 4013
```

```r
## J
length(words[grepl("^j", words) == TRUE])
```

```
## [1] 1106
```

```r
## K
length(words[grepl("^k", words) == TRUE])
```

```
## [1] 1312
```

```r
## L
length(words[grepl("^l", words) == TRUE])
```

```
## [1] 3710
```

```r
## M
length(words[grepl("^m", words) == TRUE])
```

```
## [1] 6270
```

```r
## N
length(words[grepl("^n", words) == TRUE])
```

```
## [1] 2208
```

```r
## O
length(words[grepl("^o", words) == TRUE])
```

```
## [1] 3978
```

```r
## P
length(words[grepl("^p", words) == TRUE])
```

```
## [1] 8693
```

```r
## Q
length(words[grepl("^q", words) == TRUE])
```

```
## [1] 568
```

```r
## R
length(words[grepl("^r", words) == TRUE])
```

```
## [1] 7141
```

```r
## S
length(words[grepl("^s", words) == TRUE])
```

```
## [1] 12591
```

```r
## T
length(words[grepl("^t", words) == TRUE])
```

```
## [1] 5951
```

```r
## U
length(words[grepl("^u", words) == TRUE])
```

```
## [1] 2934
```

```r
## V
length(words[grepl("^v", words) == TRUE])
```

```
## [1] 1932
```

```r
## W
length(words[grepl("^w", words) == TRUE])
```

```
## [1] 2927
```

```r
## X
length(words[grepl("^x", words) == TRUE])
```

```
## [1] 82
```

```r
## Y
length(words[grepl("^y", words) == TRUE])
```

```
## [1] 438
```

```r
## Z
length(words[grepl("^z", words) == TRUE])
```

```
## [1] 398
```


#### "Q" Without "U"

```r
noU <- words[grepl("q[^u]", words) == TRUE]
noU
```

```
##  [1] "buqsha"  "buqshas" "faqir"   "faqirs"  "qaid"    "qaids"   "qindar" 
##  [8] "qindars" "qintar"  "qintars" "qiviut"  "qiviuts" "qoph"    "qophs"
```


## Crossword Helper

```r
crossword <- function(x) {
    a <- grepl(x, words)
    return(words[a])
}

crossword("^.t..r..$")
```

```
##  [1] "athirst" "attired" "attires" "attorns" "etheric" "starred" "stearic"
##  [8] "stearin" "steered" "steerer" "stirred" "stirrer" "stirrup" "stoures"
## [15] "stourie" "uttered" "utterer" "utterly"
```


## A Better Crossword Helper


```r
crosswordPattern <- function(v, x) {
    a <- rep(".", x)
    for (k in 1:length(v)) {
        a[v[[k]]] = names(v)[k]
    }
    b <- c("^", a, "$")
    c <- paste(b, collapse = "")
    d <- grepl(c, words)
    return(words[d])
}

crosswordPattern(c(h = 1, l = 4, l = 3), 5)
```

```
##  [1] "hallo" "halls" "hello" "hells" "hillo" "hills" "hilly" "holla"
##  [9] "hollo" "holly" "hullo" "hulls"
```

#### Put into use:
![Examle Crossword](https://mail-attachment.googleusercontent.com/attachment/u/0/?ui=2&ik=3c3fb89127&view=att&th=142b194abf4b0672&attid=0.1&disp=inline&realattid=f_hop82ihu0&safe=1&zw&saduie=AG9B_P95_kyWxuKUpv_AbSlETcxe&sadet=1385958836151&sads=P6lsjlNVOlpbZMihZ2EQrEpnkps&sadssc=1)

1 Across

```r
crosswordPattern(c(l = 1, v = 3, a = 4), 4)
```

```
## [1] "lava" "leva"
```

49 Across

```r
crosswordPattern(c(n = 2, a = 3, g = 4), 4)
```

```
## [1] "snag"
```

57 Across

```r
crosswordPattern(c(e = 1, a = 3, n = 4), 4)
```

```
## [1] "elan"
```

7 Down

```r
crosswordPattern(c(a = 1, r = 2, c = 3), 4)
```

```
## [1] "arch" "arco" "arcs"
```

9 Down

```r
crosswordPattern(c(m = 1, a = 2, r = 3, a = 5), 5)
```

```
## [1] "maria"
```

38 Down

```r
crosswordPattern(c(e = 1, r = 3), 4)
```

```
##  [1] "earl" "earn" "ears" "ecru" "eery" "errs" "euro" "eyra" "eyre" "eyry"
```

51 Down

```r
crosswordPattern(c(g = 1, l = 2, a = 3, d = 4), 5)
```

```
## [1] "glade" "glads" "glady"
```

58 Down

```r
crosswordPattern(c(c = 2, e = 4), 4)
```

```
## [1] "ache" "acme" "acne" "acre" "eche"
```


## Scrabble
I added an input x which dictates how many letters the desired word will be.

```r
scrabble <- function(v, x) {
    sub1 <- words[grepl(v[1], words) == TRUE]
    sub2 <- sub1[grepl(v[2], sub1) == TRUE]
    sub3 <- sub2[grepl(v[3], sub2) == TRUE]
    sub4 <- sub3[grepl(v[4], sub3) == TRUE]
    sub5 <- sub4[grepl(v[5], sub4) == TRUE]
    sub6 <- sub5[grepl(v[6], sub5) == TRUE]
    sub7 <- sub6[grepl(v[7], sub6) == TRUE]
    if (length(sub7) > 10) {
        return(sub7[1:10])
    } else {
        a <- c(sub7, sub6, sub5, sub4)
    }
    b <- sapply(a, nchar)
    c <- as.data.frame(b, row.names = names(b))
    d <- subset(c, b == x)
    e <- row.names(d)
    return(e[1:10])
}

scrabble(c("a", "b", "c", "d", "e", "f", "g"), 7)
```

```
##  [1] "abduced" "abduces" "batched" "beached" "belaced" "blacked" "bracted"
##  [8] "brocade" "cabined" "carbide"
```

```r
scrabble(c("a", "b", "c", "d", "e", "f", "g"), 8)
```

```
##  [1] "boldface" "feedback" "abdicate" "abducens" "abducent" "abducted"
##  [7] "abidance" "abscised" "ascribed" "baccated"
```

```r
scrabble(c("a", "b", "c", "d", "e", "f", "g"), 9)
```

```
##  [1] "backfired" "barefaced" "boldfaced" "boldfaces" "confabbed"
##  [6] "feedbacks" "abdicated" "abdicates" "abidances" "abreacted"
```



