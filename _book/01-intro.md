# Motivation

::: {.rmdimportant}

A COVID Classroom

:::

<img src="_images/empty_class.jpg" style="display: block; margin: auto;" />

::: {.rmdimportant}

A Learning Management System Nightmare

:::

<img src="_images/brightspace.png" style="display: block; margin: auto;" />

::: {.rmdimportant}

Concise, Precisely Organized, Frequently Revised Assignments and Schedules

:::

Date | Topic | 				
|:-------|:------			
| 	Wednesday, February 16, 2022	| 	SEDSI in Jacksonville	| 
| 	Thursday, February 17, 2022	| 	Present at 2:45 PM	| 
| 	Friday, February 18, 2022	| 	Celebrate a successful DASI Session	| 


# Real life example

::: {.rmdimportant}

It's nice to know exactly what you did when your original data requires wrangling.

:::

Conflicts and students honors... 


```
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union
#>                               NAME TOTAL.HOURS PC.HOURS
#> 1          Greer, Patrick Sterling         3.0      3.0
#> 2          Greer, Patrick Sterling       144.0    123.0
#> 3      Thompson, Charleston Hannah         0.0      0.0
#> 4      Thompson, Charleston Hannah       142.0    122.0
#> 5  Melvin, Victor Richard-Scorsese       132.0    100.0
#> 6          Roberson, States Taylor       126.0     99.0
#> 7           Allen, Kaylee Michelle       125.0     68.0
#> 8           Phelps, Payton Elliott       117.0    114.0
#> 9       Rowley, Ella Marie Dorothy       121.0    121.0
#> 10           Smith, Michael Leston       112.0    112.0
#> 11          Taylor, Darrell Tyrese        78.0     78.0
#> 12          Wright, Alexandra Ruby       116.0    116.0
#> 13                     Adu, Tyler         80.0     80.0
#> 14           Armell, James Richard        90.0     87.0
#> 15            Bell, Carrie Abigail       120.5     99.5
#>    ADMIT.TERM
#> 1      201101
#> 2      201101
#> 3      201201
#> 4      201201
#> 5      201202
#> 6      201301
#> 7      201601
#> 8      201701
#> 9      201701
#> 10     201701
#> 11     201701
#> 12     201701
#> 13     201801
#> 14     201801
#> 15     201801
#>                           NAME TOTAL.HOURS PC.HOURS
#> 20         Drake, John Chapman          94       94
#> 21    Edwards, Nicholas Graham         101       83
#> 22             Ham, Ethan Ross          90       90
#> 23        Harmon, Luke Elliott          91       91
#> 24 Humphries, Lillian Kristine          87       78
#> 25          Julien, Christina          101       89
#> 26     Klimpel, Jake Frederick         103       97
#> 27        Leeman, Jessica Kate          92       92
#> 28      Martin, Caroline Grace         101       95
#> 29    Matthews, William McGill          96       81
#> 30  McCutchen, Caroline Louise         118       94
#>    ADMIT.TERM
#> 20     201801
#> 21     201801
#> 22     201801
#> 23     201801
#> 24     201801
#> 25     201801
#> 26     201801
#> 27     201801
#> 28     201801
#> 29     201801
#> 30     201801
```


# Some Options

> This is just a cool place to put stuff^[Footnotes are always neat. And useful. Like this one!].

Like a schedule, for example:

Footnotes are put inside the square brackets after a caret ^[]. Like this one.1

## Spring 2022

Date | Topic | 				
|:-------|:------			
| 	Monday, January 10, 2022	| 	R basics and install	| 
| 	Wednesday, January 12, 2022	| 	R basics and workflows	| 
| 	Friday, January 14, 2022	| 	QUIZ 1 	| 
| 	Monday, January 17, 2022	| 	MLK Holiday	| 
| 	Wednesday, January 19, 2022	| 	Objects, Vectors, and Arithmetic	| 
| 	Friday, January 21, 2022	| 	QUIZ 2	| 
| 	Monday, January 24, 2022	| Summaries and Subscripting	| 

## Or a figure

![](01-intro_files/figure-epub3/unnamed-chunk-4-1.png)<!-- -->

## Or an Image 

### Hero 1

<img src="_images/bob.jpg" style="display: block; margin: auto;" />

### Hero 2

<img src="_images/wilma.jpg" style="display: block; margin: auto;" />

## Or an Equation

Here is a **fun** equation for my SEDSI DASI friends:

\begin{equation} 
  f\left(k\right) = \binom{n}{k} p^k\left(1-p\right)^{n-k}
  (\#eq:binom)
\end{equation} 

## Or a table of something

### Fun example table


Table: (\#tab:unnamed-chunk-7)A table of the first 10 rows of the mtcars data.

|                  |  mpg| cyl|  disp|  hp| drat|    wt|  qsec| vs|
|:-----------------|----:|---:|-----:|---:|----:|-----:|-----:|--:|
|Mazda RX4         | 21.0|   6| 160.0| 110| 3.90| 2.620| 16.46|  0|
|Mazda RX4 Wag     | 21.0|   6| 160.0| 110| 3.90| 2.875| 17.02|  0|
|Datsun 710        | 22.8|   4| 108.0|  93| 3.85| 2.320| 18.61|  1|
|Hornet 4 Drive    | 21.4|   6| 258.0| 110| 3.08| 3.215| 19.44|  1|
|Hornet Sportabout | 18.7|   8| 360.0| 175| 3.15| 3.440| 17.02|  0|
|Valiant           | 18.1|   6| 225.0| 105| 2.76| 3.460| 20.22|  1|
|Duster 360        | 14.3|   8| 360.0| 245| 3.21| 3.570| 15.84|  0|
|Merc 240D         | 24.4|   4| 146.7|  62| 3.69| 3.190| 20.00|  1|
|Merc 230          | 22.8|   4| 140.8|  95| 3.92| 3.150| 22.90|  1|
|Merc 280          | 19.2|   6| 167.6| 123| 3.92| 3.440| 18.30|  1|


# Workflow Summary

## R (engine) and Rstudio (IDE)

<img src="_images/rstudio.png" style="display: block; margin: auto;" />

## bookdown package

<img src="_images/bookdown.png" style="display: block; margin: auto;" />

## github

<img src="_images/github.png" style="display: block; margin: auto;" />

## netlify

<img src="_images/netlify.png" style="display: block; margin: auto;" />


