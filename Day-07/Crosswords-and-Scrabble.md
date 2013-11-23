Crosswords-and-Scrabble
======================


```r
words <- readLines(url("http://dtkaplan.github.io/ScientificComputing/Syllabus/Daily/Day-07/word_list_moby_crossword-flat/word_list_moby_crossword.flat.txt"))
```

## Summarizing the List
### Report of Word Lengths
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
wordLength(1)
```

```
## [1] 0
```

```r
wordLength(2)
```

```
## [1] 85
```

```r
wordLength(3)
```

```
## [1] 908
```

```r
wordLength(4)
```

```
## [1] 3686
```

```r
wordLength(5)
```

```
## [1] 8258
```

```r
wordLength(6)
```

```
## [1] 14374
```

```r
wordLength(7)
```

```
## [1] 21727
```

```r
wordLength(8)
```

```
## [1] 26447
```

```r
wordLength(9)
```

```
## [1] 16658
```

```r
wordLength(10)
```

```
## [1] 9199
```

```r
wordLength(11)
```

```
## [1] 5296
```

```r
wordLength(12)
```

```
## [1] 3166
```

```r
wordLength(13)
```

```
## [1] 1960
```

```r
wordLength(14)
```

```
## [1] 1023
```

```r
wordLength(15)
```

```
## [1] 557
```

```r
wordLength(16)
```

```
## [1] 261
```

```r
wordLength(17)
```

```
## [1] 132
```

```r
wordLength(18)
```

```
## [1] 48
```

```r
wordLength(19)
```

```
## [1] 16
```

```r
wordLength(20)
```

```
## [1] 5
```

```r
wordLength(21)
```

```
## [1] 3
```

```r
wordLength(22)
```

```
## [1] 0
```


### 100 Longest Words
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


