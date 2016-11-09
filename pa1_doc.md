Removing NA's
-------------

The NAs are removed from the dataset

    doc <- read.csv("activity.csv")
    dox <- subset(doc,doc$steps != "NA") 

Average Steps per Day
---------------------

It is found out by splitting with respect to date and applying mean
function

`r  dox$steps <- as.numeric(dox$steps)  s <- split(dox$steps,dox$date)  l <- sapply(s, mean)  l <- as.numeric(l)  hist(l, xlab = "Average Steps Per Day",main = "Average Steps ")`

![](pa1_doc_files/figure-markdown_strict/unnamed-chunk-2-1.png) \#\#
Mean

`r   print(l)`

`##  [1]        NaN  0.4375000 39.4166667 42.0694444 46.1597222 53.5416667   ##  [7] 38.2465278        NaN 44.4826389 34.3750000 35.7777778 60.3541667   ## [13] 43.1458333 52.4236111 35.2048611 52.3750000 46.7083333 34.9166667   ## [19] 41.0729167 36.0937500 30.6284722 46.7361111 30.9652778 29.0104167   ## [25]  8.6527778 23.5347222 35.1354167 39.7847222 17.4236111 34.0937500   ## [31] 53.5208333        NaN 36.8055556 36.7048611        NaN 36.2465278   ## [37] 28.9375000 44.7326389 11.1770833        NaN        NaN 43.7777778   ## [43] 37.3784722 25.4722222        NaN  0.1423611 18.8923611 49.7881944   ## [49] 52.4652778 30.6979167 15.5277778 44.3993056 70.9270833 73.5902778   ## [55] 50.2708333 41.0902778 38.7569444 47.3819444 35.3576389 24.4687500   ## [61]        NaN`
\#\#Total Steps per Day

`r  sm <- sapply(s,sum)  sm <- as.numeric(sm)  plot(sm,ylab = "Total Steps",xlab = "Days",main = "Steps per Day")`

![](pa1_doc_files/figure-markdown_strict/unnamed-chunk-4-1.png)

    library(ggplot2)
    dox$date <- as.Date(dox$date)
    wday <- c("Monday","Tuesday","Wednesday","Thursday","Friday")
    dox$wd <- factor((weekdays(dox$date) %in% wday),levels = c(FALSE,TRUE),labels = c("weekend","weekday"))
    #dox$wd
    qplot(steps,data = dox,main = "WEEK", facets = .~wd)

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](pa1_doc_files/figure-markdown_strict/unnamed-chunk-5-1.png)
