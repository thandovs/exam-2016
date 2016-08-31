Exam 2016
================
Thando Shabalala
August 31, 2016

Question1
=========

Null Hypothesis
---------------

-   There is no relationship between oral body temperature and heart rate

Alternative Hypothesis
----------------------

-   A directly proprotional relationship exists between oral body temperature and heart rate.

Statistical test
----------------

-   ANOVA \#\#\#Assumptions of the statistical test
-   

``` r
library(tidyr)
```

    ## Warning: package 'tidyr' was built under R version 3.2.5

``` r
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.2.5

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.2.5

``` r
library(knitr)
```

    ## Warning: package 'knitr' was built under R version 3.2.5

``` r
# View and Import Dataset Question 1 CSV
q1 <- read.csv("question1.csv")
qdset <- tbl_df(q1)
q1
```

    ##     body_temperature male female
    ## 1               35.7   70     NA
    ## 2               35.8   NA     69
    ## 3               35.9   71     NA
    ## 4               35.9   NA     62
    ## 5               36.0   NA     75
    ## 6               36.1   74     NA
    ## 7               36.1   80     NA
    ## 8               36.2   73     NA
    ## 9               36.2   75     NA
    ## 10              36.2   82     NA
    ## 11              36.2   64     NA
    ## 12              36.2   NA     66
    ## 13              36.2   NA     68
    ## 14              36.3   69     NA
    ## 15              36.3   70     NA
    ## 16              36.3   68     NA
    ## 17              36.3   72     NA
    ## 18              36.3   78     NA
    ## 19              36.3   NA     57
    ## 20              36.4   70     NA
    ## 21              36.4   75     NA
    ## 22              36.4   74     NA
    ## 23              36.4   69     NA
    ## 24              36.4   73     NA
    ## 25              36.4   NA     61
    ## 26              36.5   77     NA
    ## 27              36.5   NA     84
    ## 28              36.5   NA     61
    ## 29              36.6   58     NA
    ## 30              36.6   73     NA
    ## 31              36.6   65     NA
    ## 32              36.6   74     NA
    ## 33              36.6   76     NA
    ## 34              36.6   72     NA
    ## 35              36.6   NA     77
    ## 36              36.6   NA     62
    ## 37              36.6   NA     71
    ## 38              36.6   NA     68
    ## 39              36.6   NA     69
    ## 40              36.6   NA     79
    ## 41              36.7   78     NA
    ## 42              36.7   71     NA
    ## 43              36.7   74     NA
    ## 44              36.7   67     NA
    ## 45              36.7   64     NA
    ## 46              36.7   78     NA
    ## 47              36.7   73     NA
    ## 48              36.7   67     NA
    ## 49              36.7   NA     76
    ## 50              36.7   NA     87
    ## 51              36.7   NA     78
    ## 52              36.7   NA     73
    ## 53              36.7   NA     89
    ## 54              36.7   NA     81
    ## 55              36.8   66     NA
    ## 56              36.8   64     NA
    ## 57              36.8   71     NA
    ## 58              36.8   72     NA
    ## 59              36.8   86     NA
    ## 60              36.8   72     NA
    ## 61              36.8   NA     73
    ## 62              36.8   NA     64
    ## 63              36.8   NA     65
    ## 64              36.8   NA     73
    ## 65              36.8   NA     69
    ## 66              36.8   NA     57
    ## 67              36.8   NA     79
    ## 68              36.8   NA     78
    ## 69              36.8   NA     80
    ## 70              36.9   68     NA
    ## 71              36.9   70     NA
    ## 72              36.9   82     NA
    ## 73              36.9   84     NA
    ## 74              36.9   68     NA
    ## 75              36.9   71     NA
    ## 76              36.9   NA     79
    ## 77              36.9   NA     81
    ## 78              36.9   NA     73
    ## 79              36.9   NA     74
    ## 80              36.9   NA     84
    ## 81              36.9   NA     83
    ## 82              37.0   77     NA
    ## 83              37.0   78     NA
    ## 84              37.0   83     NA
    ## 85              37.0   66     NA
    ## 86              37.0   70     NA
    ## 87              37.0   82     NA
    ## 88              37.0   NA     82
    ## 89              37.0   NA     85
    ## 90              37.0   NA     86
    ## 91              37.0   NA     77
    ## 92              37.1   73     NA
    ## 93              37.1   78     NA
    ## 94              37.1   78     NA
    ## 95              37.1   81     NA
    ## 96              37.1   78     NA
    ## 97              37.1   NA     72
    ## 98              37.1   NA     79
    ## 99              37.1   NA     59
    ## 100             37.1   NA     64
    ## 101             37.1   NA     65
    ## 102             37.1   NA     82
    ## 103             37.1   NA     64
    ## 104             37.1   NA     70
    ## 105             37.1   NA     83
    ## 106             37.1   NA     89
    ## 107             37.1   NA     69
    ## 108             37.1   NA     73
    ## 109             37.1   NA     84
    ## 110             37.2   80     NA
    ## 111             37.2   75     NA
    ## 112             37.2   79     NA
    ## 113             37.2   81     NA
    ## 114             37.2   NA     76
    ## 115             37.2   NA     79
    ## 116             37.2   NA     81
    ## 117             37.3   71     NA
    ## 118             37.3   83     NA
    ## 119             37.3   NA     80
    ## 120             37.3   NA     74
    ## 121             37.3   NA     77
    ## 122             37.3   NA     66
    ## 123             37.4   63     NA
    ## 124             37.4   70     NA
    ## 125             37.4   NA     68
    ## 126             37.4   NA     77
    ## 127             37.5   75     NA
    ## 128             37.7   NA     79
    ## 129             37.8   NA     78
    ## 130             38.2   NA     77

``` r
# Plots
plot(q1$male ~ q1$body_temperature,
     col="pink",main = "Mean oral body temperature and heart rate at rest in male and female students",ylab = " Heart Rate",xlab = "Oral Body Temperature")
points(q1$female)
legend(37.5,85, c("Male", "Female"), fill = c("pink", "black"))
```

![](Readme_files/figure-markdown_github/question1-1.png) \#\#Outcome Analysis \* Inferences with this data across sexes must be cautious as most of the heart rate inputs for the females are missing \* However, considering only male heart rates, the data suggestss that there is a somewhat directly proportional relationship between

Question2
=========

Null Hypothesis
---------------

-   There is no relationship between handednes and ataxic walking in intoxicated individuals

Alternative Hypothesis
----------------------

-   Ataxic walking in intoxicated individuals and hadedness are related. Individuals tend to orientate themselves in accordance with the dominant side.

Statistical Test
----------------

-   Wilcoxin rank-sum \#\#\#Assumptions of the statistical test
-   independent errors
-   data is unmatched (as comparison across are being made for example)
-   samples are drawn from populations witht the same shape distribution

``` r
library(tidyr)
library(dplyr)
library(ggplot2)
library(knitr)

# View and Import Dataset Question 2 CSV

q2 <- read.csv("question2.csv")
q2data<- tbl_df(q2)
q2data
```

    ## # A tibble: 151 × 5
    ##       id   sex handedness first_stumble final_position
    ##    <int> <int>      <int>         <int>          <int>
    ## 1      1     1          1             1              1
    ## 2      2     1          1             1              1
    ## 3      3     0          1             1              1
    ## 4      4     1          1             1              0
    ## 5      5     1          1             0              0
    ## 6      6     1          0             0              1
    ## 7      7     0          0             0              0
    ## 8      8     0          0             0              0
    ## 9      9     1          0             1              1
    ## 10    10     0          0             0              0
    ## # ... with 141 more rows

``` r
# Plots
boxplot(q2data$first_stumble ~ q2data$handedness)
```

![](Readme_files/figure-markdown_github/question2-1.png)

``` r
par(mfrow = c(1,2),mar = c(4, 4, 2, 1),oma = c(0, 0, 1, 0)) 

mosaicplot(q2data$handedness ~ q2data$first_stumble, main = "Handedness against position of first stumble", ylab = "First Stumble (1= rightwards, 2 = leftwards)", xlab = "Handedness (1 = right-handed, 2 = left-handed)")

mosaicplot(q2data$final_position ~ q2data$handedness,main = "Handedness against final position",ylab = "Final Stimble (1= rightwards, 2 = leftwards)",xlab = "Handedness (1 = right-handed, 2 = left-handed)")
```

![](Readme_files/figure-markdown_github/question2-2.png)

``` r
wilcox.test(first_stumble ~ handedness, data = q2data, paired = FALSE)
```

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  first_stumble by handedness
    ## W = 1661, p-value = 3.266e-07
    ## alternative hypothesis: true location shift is not equal to 0

``` r
wilcox.test(final_position~handedness,data = q2data,paired = FALSE)
```

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  final_position by handedness
    ## W = 2376, p-value = 0.04058
    ## alternative hypothesis: true location shift is not equal to 0

``` r
par(mfrow = c(1,1),mar = c(4, 4, 2, 1),oma = c(0, 0, 1, 0))            
```

Outcome Analysis
----------------

-   The null hypothesis may be rejected as handedness was shown to be related with first stumble (*p* &lt;0.05) and final position (*p* = 0.04). These results illustrate that intoxicated individuals are more likely to exhibit ataxic gait that is skewed to her/his dominant side.

Question3
=========

Null Hypothesis
---------------

-   There is nor relationsip between running time and calories

Alternative Hypothesis
----------------------

-   There is a directly proportional relatiolnship between running time and caloreies consumed

Statistical Test(s)
-------------------

-   Linear Regression \#\#\#Assumptions of the statistical test
-   linear relationship exists between the variables
-   independent observations
-   x variable measured without error
-   normally distributed residuals
-   homoskedastic residuals

``` r
library(tidyr)
library(dplyr)
library(ggplot2)
library(knitr)

# View and Import Dataset Question 3 CSV
q3 <- read.csv("question3.csv")
q3cal <- tbl_df(q3)
q3cal
```

    ## # A tibble: 19 × 3
    ##      run  time calories
    ##    <int> <int>    <int>
    ## 1      1  2169      319
    ## 2      2  1986      384
    ## 3      3  1979      398
    ## 4      4  1937      359
    ## 5      5  2093      366
    ## 6      6  1924      388
    ## 7      7  1949      411
    ## 8      8  1879      423
    ## 9      9  2106      373
    ## 10    10  2019      418
    ## 11    11  1957      446
    ## 12    12  1926      400
    ## 13    13  2134      347
    ## 14    14  2174      334
    ## 15    15  2088      378
    ## 16    16  1903      368
    ## 17    17  2146      320
    ## 18    18  2059      326
    ## 19    19  2057      302

``` r
# Plot

plot(q3cal$calories ~ q3cal$time,
      main = "Relationship between an amateur runner's running time and calories consumed", ylab = "Calories Consumed (cal)", xlab = "Running Time (s)")
```

![](Readme_files/figure-markdown_github/question3-1.png)

``` r
p <- qplot(x = time, y = calories,data = q3cal,main = "Relationship between an amateur runner's running time and calories consumed",ylab = "Calories Consumed (cal)",xlab = "Running Time (s)")

#Pearson Correlation and print the summary statistics

q3cal.cor <- with(q3cal, cor.test(method = 'pearson', x = time, y = calories))
q3cal.cor
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  time and calories
    ## t = -3.7715, df = 17, p-value = 0.001522
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.8642170 -0.3183295
    ## sample estimates:
    ##        cor 
    ## -0.6749491

``` r
#Annotate r and p values onto the plot

p + annotate("text", x = 2150, y = 420, label = "r = -0.7") + annotate("text", x = 2150, y = 410, label = "p = 0.002")
```

![](Readme_files/figure-markdown_github/question3-2.png)

``` r
# View
par(mfrow = c(1,2),mar = c(4, 4, 2, 1),oma = c(0, 0, 1, 0))

#Summary of linear regression
q3cal.reg <- lm(calories ~ time, data = q3cal)
summary(q3cal.reg)
```

    ## 
    ## Call:
    ## lm(formula = calories ~ time, data = q3cal)
    ## 
    ## Residuals:
    ##    Min     1Q Median     3Q    Max 
    ## -60.76 -15.09   4.04  15.67  55.21 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 939.36422  150.70365   6.233 9.09e-06 ***
    ## time         -0.28031    0.07432  -3.772  0.00152 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 30.17 on 17 degrees of freedom
    ## Multiple R-squared:  0.4556, Adjusted R-squared:  0.4235 
    ## F-statistic: 14.22 on 1 and 17 DF,  p-value: 0.001522

``` r
#Plot

plot(x = q3cal.reg$fitted.values,y = q3cal.reg$residuals,xlab = "Fitted Values",ylab = "Residuals",main = "Homoskedasticity of residuals")
abline(h = 0)

# 
qqnorm(q3cal.reg$residuals, main = "Normal residula distribution")
qqline(q3cal.reg$residuals)

# Overall Title
mtext("Regression analysis", outer = TRUE)
```

![](Readme_files/figure-markdown_github/question3-3.png) \#\#Outcome Analysis \* The data fits all assumptions of a linear regression, including homoskedasticity and normal distribution of the residuals. \* The variables have a fairly strong negative correlation (-0.07). Because the *p* value is small (0.002), the null hypothesis can be rejected. \* CONCLUSION: running time and calorie consumption are inversely proportional

question4
=========

``` r
foo <- rnorm(10000, mean = 60, sd = 3) # final mark
bar <- rnorm(10000, mean = 68, sd = 5) # project mark
baz <- rep(seq(from = 1997, to = 2006), each = 1) # years

years <- sample(baz, 150, replace = TRUE,prob = c(0.05, 0.05, 0.08, 0.08, 0.1, 0.13, 0.14, 0.13, 0.12, 0.12))

projectmark <- sample(bar, 150, replace = TRUE)

finalmark <- sample(foo, 150, replace = TRUE)

q4plot <- data_frame(year = years,projectmark = round(projectmark, 1),finalmark = round(finalmark, 1)) %>%
arrange(years)

# View
q4plot
```

    ## # A tibble: 150 × 3
    ##     year projectmark finalmark
    ##    <int>       <dbl>     <dbl>
    ## 1   1997        62.8      60.6
    ## 2   1997        63.6      60.7
    ## 3   1997        74.6      57.8
    ## 4   1997        75.1      61.8
    ## 5   1997        62.0      61.4
    ## 6   1997        71.0      58.1
    ## 7   1997        78.2      63.2
    ## 8   1998        63.3      56.9
    ## 9   1998        69.5      61.9
    ## 10  1998        64.5      62.7
    ## # ... with 140 more rows

``` r
# Tidying Data
data_tidy <- q4plot %>%
    mutate(year = factor(year)) %>%
    gather(key = key, value = value, -year) %>%
    arrange(year)

# Plot
with (data_tidy, boxplot(value ~ key,main = "Marks",ylab = "Percentage"))
```

![](Readme_files/figure-markdown_github/question4-1.png)
