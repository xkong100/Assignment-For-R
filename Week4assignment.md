UK gas analysis
================

load the UKgas data, which is included with the ggplot2 packages.

``` r
#install.packages("ggplot2")
require(ggplot2)
```

    ## Loading required package: ggplot2

``` r
gas <- read.csv("UKgas.csv", header=TRUE)
head(gas)
```

    ##   X    time UKgas
    ## 1 1 1960.00 160.1
    ## 2 2 1960.25 129.7
    ## 3 3 1960.50  84.8
    ## 4 4 1960.75 120.1
    ## 5 5 1961.00 160.1
    ## 6 6 1961.25 124.9

``` r
# Identify which variables in the gas dataset are numeric, and which
# variables are categorical
str(gas)
```

    ## 'data.frame':    108 obs. of  3 variables:
    ##  $ X    : int  1 2 3 4 5 6 7 8 9 10 ...
    ##  $ time : num  1960 1960 1960 1961 1961 ...
    ##  $ UKgas: num  160.1 129.7 84.8 120.1 160.1 ...

``` r
ggplot(gas,aes(y=UKgas, x=1)) + geom_boxplot()
```

![](Week4assignment_files/figure-markdown_github/unnamed-chunk-2-1.png)

``` r
hist(gas$UKgas, main = "UKgas Histogram", xlab = "gas")
```

![](Week4assignment_files/figure-markdown_github/unnamed-chunk-2-2.png)

``` r
ggplot(gas, aes(x= time, y= UKgas))+ geom_point()
```

![](Week4assignment_files/figure-markdown_github/unnamed-chunk-2-3.png)

By observing the graphs, we can conclude that the meadian of UKgas consumption is about 200. Most people would consume gas around 100 to 200. Our graph is skewed to the left that means the mean UKgas consumption is less than its median. From the plot graph, we can clearly conclude that people consume gas more and more as the time is more approaching to 21st century becasue the technology is improving year by year, people heavily rely on the transportation such as cars.
