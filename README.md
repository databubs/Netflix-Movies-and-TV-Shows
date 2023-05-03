# Introduction
Hey its Bobby and in this case study I will be focusing on visualizations briefly explaining my thought process while doing this using R Studio

## Interesting Task Ideas - Suggestions from Kaggle

Understanding what content is available in different countries

Identifying similar content by matching text-based features

Network analysis of Actors / Directors and find interesting insights

Does Netflix has more focus on TV Shows than movies in recent years.


# Process Data
[Netflix/TV Shows Data set](https://www.kaggle.com/datasets/shivamb/netflix-shows) 

1. Read CSV file into R Studio.
```r
netflix_data <- read.csv("C:/Users/Bobby/Desktop/Netflix_Dataset/netflix_titles.csv")
```

2. Check the data types and varaibles
```r
str(netflix)
```

3. Check the summary of the release years
```r
summary(netflix$release_year)
```

4. What does this tell us about the release years?
```r
 Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   1925    2013    2017    2014    2019    2021 
```

5. How many movies and TV shows do we currently have in our dataset?
```r
table(netflix$type)

  Movie TV Show 
   6131    2676 
```

# Cleaning Data

In order to summarize everything we would need to remove any values or variables that doesn't relate to this dataset
ls(netflix_data)
 [1] "cast"         "country"      "date_added"   "description" 
 [5] "director"     "duration"     "listed_in"    "rating"      
 [9] "release_year" "show_id"      "title"        "type"      





# Share

What we currently have right now. More is coming!

![alt text](https://github.com/databubs/Netflix-Movies-and-TV-Shows/blob/main/Release_Year.png)

![alt text](https://github.com/databubs/Netflix-Movies-and-TV-Shows/blob/main/TopCountries.png)
