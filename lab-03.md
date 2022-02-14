Lab 03 - Nobel laureates
================
John T. Bennett
Feb. 10, 2022

### Load packages and data

``` r
library(tidyverse) 
```

``` r
nobel <- read_csv("data/nobel.csv")
```

## Exercises

### Exercise 1

There are 935 observations in the dataset. The number of variables in
the dataset is 26. Each row represents one Nobel laureate.

``` r
View(nobel)
```

### Exercise 2

    Create a new data frame called nobel_living that filters for:
    -laureates for whom country is available
    -laureates who are people as opposed to organizations (organizations are denoted with "org" as their gender)
    -laureates who are still alive (their died_date is NA)

     Confirm that once you have filtered for these characteristics you are left with a data frame with 228 observations, once again using inline code.
     
     **JTB Note: In order to see the actual 228x26 tibble, I've entered the code without the dataframe command (myDataframe <-) immediately below. Then, below that, I've entered the code with the dataframe command. 

``` r
nobel %>%
  filter(!is.na(country),
  gender != "org",
  is.na(died_date))
```

    ## # A tibble: 228 × 26
    ##       id firstname   surname  year category affiliation city  country born_date 
    ##    <dbl> <chr>       <chr>   <dbl> <chr>    <chr>       <chr> <chr>   <date>    
    ##  1    68 Chen Ning   Yang     1957 Physics  Institute … Prin… USA     1922-09-22
    ##  2    69 Tsung-Dao   Lee      1957 Physics  Columbia U… New … USA     1926-11-24
    ##  3    95 Leon N.     Cooper   1972 Physics  Brown Univ… Prov… USA     1930-02-28
    ##  4    97 Leo         Esaki    1973 Physics  IBM Thomas… York… USA     1925-03-12
    ##  5    98 Ivar        Giaever  1973 Physics  General El… Sche… USA     1929-04-05
    ##  6    99 Brian D.    Joseph…  1973 Physics  University… Camb… United… 1940-01-04
    ##  7   101 Antony      Hewish   1974 Physics  University… Camb… United… 1924-05-11
    ##  8   103 Ben R.      Mottel…  1975 Physics  Nordita     Cope… Denmark 1926-07-09
    ##  9   106 Samuel C.C. Ting     1976 Physics  Massachuse… Camb… USA     1936-01-27
    ## 10   107 Philip W.   Anders…  1977 Physics  Bell Telep… Murr… USA     1923-12-13
    ## # … with 218 more rows, and 17 more variables: died_date <date>, gender <chr>,
    ## #   born_city <chr>, born_country <chr>, born_country_code <chr>,
    ## #   died_city <chr>, died_country <chr>, died_country_code <chr>,
    ## #   overall_motivation <chr>, share <dbl>, motivation <chr>,
    ## #   born_country_original <chr>, born_city_original <chr>,
    ## #   died_country_original <chr>, died_city_original <chr>, city_original <chr>,
    ## #   country_original <chr>

``` r
nobel_living <- nobel %>%
  filter(!is.na(country),
  gender != "org",
  is.na(died_date))
```

### Exercise 3

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 4

Create a new variable called born_country_us that has the value “USA” if
the laureate is born in the US, and “Other” otherwise. How many of the
winners are born in the US?

### Exercise 5

Add a second variable to your visualization from Exercise 3 based on
whether the laureate was born in the US or not. Based on your
visualization, do the data appear to support Buzzfeed’s claim? Explain
your reasoning in 1-2 sentences.

    Your final visualization should contain a facet for each category.
    Within each facet, there should be a bar for whether the laureate won the award in the US or not.
    Each bar should have segments for whether the laureate was born in the US or not.

### Exercise 6

In a single pipeline, filter for laureates who won their prize in the
US, but were born outside of the US, and then create a frequency table
(with the count() function) for their birth country (born_country) and
arrange the resulting data frame in descending order of number of
observations for each country. Which country is the most common?
