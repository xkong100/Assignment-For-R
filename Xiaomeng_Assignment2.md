Xiaomeng Kong's Week 2 Assignment
================

The following is my code

``` r
factorial_formula <- function(a){
  i<-1
  fact<-1
  max <- a
  while (i <= a){
    fact<- i * fact
    i <- i+1
  }
  fact
}
combination_formula <- function(x,n){
  return(factorial_formula(x)/(factorial_formula(n) * factorial_formula(x-n)))
}
```

Here are some experiments. 5 choose 3 is

    ## [1] 10

10 choose 5 is

    ## [1] 252
