Tool Tips
============


## From R to HTML
<style>
.hiword {background:pink;}
</style>
This <span class='hiword' title='Example of tooltip!'>word</span> has a tooltip.


```r
formatWord <- function(words, translation, class) {
    if (is.na(translation)) 
        return(words)
    wordsanswer <- paste("<span class='", class, "' ", sep = "")
    translationanswer <- paste(wordsanswer, "title='", translation, "'>", sep = "")
    classanswer <- paste(translationanswer, words, "</span>", sep = "")
    return(classanswer)
}
```



```r
formatWord("Hello", "hi there!", class = "hiword")
```

```
## [1] "<span class='hiword' title='hi there!'>Hello</span>"
```


```r
cat(formatWord("Hello", "hi there!", class = "hiword"), "to", "all", "of", "you", 
    "in", formatWord("Television Land.", "TV viewers", class = "hiword"))
```

<span class='hiword' title='hi there!'>Hello</span> to all of you in <span class='hiword' title='TV viewers'>Television Land.</span>

## Your Task

```r
formatString <- function(words, tips, styles) {
    results <- c()
    for (k in 1:length(words)) {
        results[k] <- formatWord(words[k], tips[k], styles[k])
    }
    return(cat(results))
}

formatString(c("How", "now", "brown", "cow", "!"), c("How are you doing?", NA, 
    "Why brown?", "bovine", "enthusiasm"), c("hiword", "", "brown", "blue", 
    "hiword"))
```

<span class='hiword' title='How are you doing?'>How</span> now <span class='brown' title='Why brown?'>brown</span> <span class='blue' title='bovine'>cow</span> <span class='hiword' title='enthusiasm'>!</span>

```r
formatString(c("Shine", "On", "You", "Crazy", "Diamond", "..."), c("Like the sun!", 
    "on what?", "No me!", "who Syd?", "Valuable!", "Alright lets hear it!"), 
    c("fancyfont", "fancyfont", "fancyfont", "fancyfont", "fancyfont"))
```

<span class='fancyfont' title='Like the sun!'>Shine</span> <span class='fancyfont' title='on what?'>On</span> <span class='fancyfont' title='No me!'>You</span> <span class='fancyfont' title='who Syd?'>Crazy</span> <span class='fancyfont' title='Valuable!'>Diamond</span> <span class='NA' title='Alright lets hear it!'>...</span>

<style>
.hiword {background:pink;}
.brown {background:brown;}
.blue {background:lightslateblue;}
.fancyfont {font: oblique 40px cursive;}
</style>
