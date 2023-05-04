# Introduction
Hey its Bobby and in this case study I will be focusing on visualizations briefly explaining my thought process while using R Studio. You can follow me step by step :)
If you have any questions feel free to contact me at CHIENG@LIVE.CA

## Interesting Task Ideas - Suggestions from Kaggle

Understanding what content is available in different countries.

Network analysis of Actors / Directors and find interesting insights.

Does Netflix has more focus on TV Shows than movies in recent years.


# Process Data
[Netflix/TV Shows Data set](https://www.kaggle.com/datasets/shivamb/netflix-shows) 

1. Read CSV file into R Studio. **Your file location has a different name than mine**
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

Lets check out our Netflix_Data column and which ones are relevant or not.

```r
ls(netflix_data)
 [1] "cast"         "country"      "date_added"   "description" 
 [5] "director"     "duration"     "listed_in"    "rating"      
 [9] "release_year" "show_id"      "title"        "type"      
 ```
 
I will be removing "show_ID, and "description to make our anaylsis more simple to understand
```r
netflix_data <- select(netflix_data, -show_id, -description)
```

Removing duration and rating
```r
netflix_data <- select(netflix_data, -duration, -rating)
```

Everytime we remove a column we can double check it's removed

```r
 ls(netflix_data)
[1] "cast"         "country"      "date_added"   "director"    
[5] "listed_in"    "release_year" "title"        "type"
```

We will need to group the data by release year to create a scatterplot

```r
library(dplyr)
netflix_data_year <- netflix_data %>% group_by(release_year)
```

```r
Plot Code:

library(ggplot2)
ggplot(netflix_data_year_count, aes(x = release_year, y = count)) +
  geom_point() +
  labs(x = "Release Year", y = "Number of Titles") +
  ggtitle("Number of Netflix Titles by Release Year")
  ```


Lets find the top 10 countries with MOST content

Group data by country

```r
netflix_data_country <- netflix_data %>% group_by(country)
```

```r
netflix_data_country_count <- netflix_data_country %>% summarize(count = n())
```

Sorting the  data in DESC order

```r
netflix_data_country_count_sorted <- netflix_data_country_count %>% 
  arrange(desc(count))
```

```r
Plot Code:

library(ggplot2)
ggplot(top_10_countries, aes(x = reorder(country, count), y = count)) +
  geom_bar(stat = "identity", fill = "darkblue") +
  labs(x = "Country", y = "Number of Titles") +
  ggtitle("Top 10 Countries with Most Content on Netflix")
```




# Share/Act

![alt text](https://github.com/databubs/Netflix-Movies-and-TV-Shows/blob/main/Top_Content.png)

![alt text](https://github.com/databubs/Netflix-Movies-and-TV-Shows/blob/main/Release_By_Year.png)

![alt text](https://github.com/databubs/Netflix-Movies-and-TV-Shows/blob/main/Release_Year.png)

