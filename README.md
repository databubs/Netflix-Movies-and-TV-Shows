# Introduction
Hey its Bobby and in this case study I will be focusing on visualizations briefly explaining my thought process while doing this.

## Interesting Task Ideas - Suggestions from Kaggle

Understanding what content is available in different countries

Identifying similar content by matching text-based features

Network analysis of Actors / Directors and find interesting insights

Does Netflix has more focus on TV Shows than movies in recent years.


# Process Data

[Netflix/TV Shows Data set](https://www.kaggle.com/datasets/shivamb/netflix-shows) 
```r
netflix <- read.csv("netflix_titles.csv", header = TRUE)
```


```r
str(netflix)
```


```r
summary(netflix$release_year)
```

```r
 Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   1925    2013    2017    2014    2019    2021 
```

```r
table(netflix$type)

  Movie TV Show 
   6131    2676 
```


