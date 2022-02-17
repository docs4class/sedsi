# Lab 3: `coronavirus` visualization, data wrangling, and dates

## Overview

The package is available on GitHub [here](https://github.com/RamiKrispin/coronavirus) and is updated daily.

I use the `coronavirus` package and use the `coronavirus::update_data()` function to keep the data current.  This also has the dates preformatted which can be nice.


## Let's look like Applied Analytics Superstars and make some neat visuals.


```r
coronavirus::update_dataset()
#> Rows: 633609 Columns: 15
#> -- Column specification ------------------------------------
#> Delimiter: ","
#> chr  (8): province, country, type, iso2, iso3, combined_...
#> dbl  (6): lat, long, cases, uid, code3, population
#> date (1): date
#> 
#> i Use `spec()` to retrieve the full column specification for this data.
#> i Specify the column types or set `show_col_types = FALSE` to quiet this message.
#> No updates are available
```



```r
library(coronavirus)
library(dplyr)
library(ggplot2)
```

I'd recommend you always start by trying to understand a bit about the data.


```r
head(coronavirus)
#>         date province country     lat      long      type
#> 1 2020-01-22  Alberta  Canada 53.9333 -116.5765 confirmed
#> 2 2020-01-23  Alberta  Canada 53.9333 -116.5765 confirmed
#> 3 2020-01-24  Alberta  Canada 53.9333 -116.5765 confirmed
#> 4 2020-01-25  Alberta  Canada 53.9333 -116.5765 confirmed
#> 5 2020-01-26  Alberta  Canada 53.9333 -116.5765 confirmed
#> 6 2020-01-27  Alberta  Canada 53.9333 -116.5765 confirmed
#>   cases   uid iso2 iso3 code3    combined_key population
#> 1     0 12401   CA  CAN   124 Alberta, Canada    4413146
#> 2     0 12401   CA  CAN   124 Alberta, Canada    4413146
#> 3     0 12401   CA  CAN   124 Alberta, Canada    4413146
#> 4     0 12401   CA  CAN   124 Alberta, Canada    4413146
#> 5     0 12401   CA  CAN   124 Alberta, Canada    4413146
#> 6     0 12401   CA  CAN   124 Alberta, Canada    4413146
#>   continent_name continent_code
#> 1  North America             NA
#> 2  North America             NA
#> 3  North America             NA
#> 4  North America             NA
#> 5  North America             NA
#> 6  North America             NA
```

For example, what does this summary let us know?


```r
summary(coronavirus$cases)
#>      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
#> -30974748         0         0       669        29   1368563
```

1. Can you create a visual showing the cases over time for Russia, Spain, US, and Venezuela?
Also, why might `filter(cases >= 0)` be worth using? 

![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-4-1.png)<!-- -->

2. Can you show deaths over time for Russia, Spain, US, and Venezuela?  And can you play with your geoms and make something neat?

![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-5-1.png)<!-- -->

3. Now let's do a plot of COVID rate (# confirmed cases / population).  Something like this. 

![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-6-1.png)<!-- -->

4. What is and **is not** useful about the previous illustration?  

5. Make a chart with cumulative cases.  Something like this:

![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-7-1.png)<!-- -->

6.  With a little more time and a few extra packages, we **could** make a graph prettier.  Try.


```r
library(scales)
library(ggrepel)
library(glue)
library(lubridate)
```


![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-9-1.png)<!-- -->


7. Now let's **really** have some fun.  Let's illustrate death rates relative to confirmed cases.  Why is this more challenging than anything we've done so far in this lab?  We're going to have to make this data **tidy**.  

One way to play this game.



Let's make a little table of just date, country, and deaths (with a meaningful variable name), and then count observations by coutry just to make sure eveything looks nice.


```
#>         date country deaths
#> 1 2020-01-22  Russia      0
#> 2 2020-01-23  Russia      0
#> 3 2020-01-24  Russia      0
#> 4 2020-01-25  Russia      0
#> 5 2020-01-26  Russia      0
#> 6 2020-01-27  Russia      0
#>     country   n
#> 1    Russia 757
#> 2     Spain 754
#> 3        US 757
#> 4 Venezuela 756
```

Let's make a little table of just confirmed cases.


```
#>         date country confirmed
#> 1 2020-01-22  Russia         0
#> 2 2020-01-23  Russia         0
#> 3 2020-01-24  Russia         0
#> 4 2020-01-25  Russia         0
#> 5 2020-01-26  Russia         0
#> 6 2020-01-27  Russia         0
#>     country   n
#> 1    Russia 757
#> 2     Spain 757
#> 3        US 757
#> 4 Venezuela 757
```

Let's join these together. I use `left_join`.  



```
#>         date country deaths confirmed
#> 1 2020-01-22  Russia      0         0
#> 2 2020-01-23  Russia      0         0
#> 3 2020-01-24  Russia      0         0
#> 4 2020-01-25  Russia      0         0
#> 5 2020-01-26  Russia      0         0
#> 6 2020-01-27  Russia      0         0
#>     country   n
#> 1    Russia 757
#> 2     Spain 757
#> 3        US 757
#> 4 Venezuela 757
```

Let's add some cumulative statistics as well.


```
#>         date country deaths confirmed cumulative_cases
#> 1 2020-01-22  Russia      0         0                0
#> 2 2020-01-23  Russia      0         0                0
#> 3 2020-01-24  Russia      0         0                0
#> 4 2020-01-25  Russia      0         0                0
#> 5 2020-01-26  Russia      0         0                0
#> 6 2020-01-27  Russia      0         0                0
#>   cumulative_deaths rate
#> 1                 0    0
#> 2                 0    0
#> 3                 0    0
#> 4                 0    0
#> 5                 0    0
#> 6                 0    0
```

Now we can plot some more fun stuff.



```r

ggplot(data = df3,
       mapping = aes(x = date,
                     y = rate,
                     color = country)) +
  geom_line()
```

![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-15-1.png)<!-- -->

```r

summary(df3)
#>       date              country              deaths      
#>  Min.   :2020-01-22   Length:3028        Min.   :   0.0  
#>  1st Qu.:2020-07-29   Class :character   1st Qu.:   5.0  
#>  Median :2021-02-03   Mode  :character   Median : 126.0  
#>  Mean   :2021-02-03                      Mean   : 452.7  
#>  3rd Qu.:2021-08-11                      3rd Qu.: 639.2  
#>  Max.   :2022-02-16                      Max.   :4442.0  
#>                                          NA's   :4       
#>    confirmed         cumulative_cases    cumulative_deaths
#>  Min.   : -74937.0   Min.   :        0   Min.   :     0   
#>  1st Qu.:    461.5   1st Qu.: 14445698   1st Qu.: 16977   
#>  Median :   7814.0   Median : 25190092   Median : 99431   
#>  Mean   :  34303.5   Mean   : 43523860   Mean   :135068   
#>  3rd Qu.:  28170.0   3rd Qu.:103362932   3rd Qu.:248203   
#>  Max.   :1368563.0   Max.   :103870974   Max.   :364273   
#>                                          NA's   :2147     
#>       rate          
#>  Min.   :-0.036576  
#>  1st Qu.: 0.004568  
#>  Median : 0.012750  
#>  Mean   : 0.021680  
#>  3rd Qu.: 0.023227  
#>  Max.   : 3.840391  
#>  NA's   :4
library(scales)
library(ggrepel)
library(glue)
library(lubridate)
as_of_date <- df3 %>% 
  summarise(max(date)) %>% 
  pull()
as_of_date_formatted <- glue("{wday(as_of_date, label = TRUE)}, {month(as_of_date, label = TRUE)} {day(as_of_date)}, {year(as_of_date)}")

ggplot(data = df3,
       mapping = aes(x = date, 
                     y = cumulative_cases, 
                     color = country)) +
  # represent cumulative cases with lines
  geom_line(size = 0.7, alpha = 0.8) +
  # add points to line endings
  geom_point() +
  # add country labels, nudged above the lines
  # geom_label_repel(nudge_y = 1, direction = "y", hjust = 1) + 
  # turn off legend
  guides(color = FALSE) +
  # use pretty colors
  scale_color_viridis_d() +
  # better formatting for y-axis
  scale_y_continuous(labels = label_comma()) +
  # use minimal theme
  theme_minimal() +
  # customize labels
  labs(
    x = "My pretty Lab 3 visual",
    y = "Cumulative number of deaths",
    title = "Cumulative deaths from COVID-19, selected countries",
    subtitle = glue("Data as of", as_of_date_formatted, .sep = " "),
    caption = "Source: github.com/RamiKrispin/coronavirus"
  )
```

![](105-coronavirus_lab_files/figure-epub3/unnamed-chunk-15-2.png)<!-- -->

# Thoughts?  Questions?  Discussion?

## Thank you for your time!
