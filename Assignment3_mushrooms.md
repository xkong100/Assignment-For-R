Assignment3 Mushrooms
================

The following is my code:

``` r
theUrl <- "https://archive.ics.uci.edu/ml/machine-learning-databases/mushroom/agaricus-lepiota.data"
mushrooms <- read.table(file = theUrl, header = FALSE, sep = ",")
head(mushrooms)
```

    ##   V1 V2 V3 V4 V5 V6 V7 V8 V9 V10 V11 V12 V13 V14 V15 V16 V17 V18 V19 V20
    ## 1  p  x  s  n  t  p  f  c  n   k   e   e   s   s   w   w   p   w   o   p
    ## 2  e  x  s  y  t  a  f  c  b   k   e   c   s   s   w   w   p   w   o   p
    ## 3  e  b  s  w  t  l  f  c  b   n   e   c   s   s   w   w   p   w   o   p
    ## 4  p  x  y  w  t  p  f  c  n   n   e   e   s   s   w   w   p   w   o   p
    ## 5  e  x  s  g  f  n  f  w  b   k   t   e   s   s   w   w   p   w   o   e
    ## 6  e  x  y  y  t  a  f  c  b   n   e   c   s   s   w   w   p   w   o   p
    ##   V21 V22 V23
    ## 1   k   s   u
    ## 2   n   n   g
    ## 3   n   n   m
    ## 4   k   s   u
    ## 5   n   a   g
    ## 6   k   n   g

``` r
# create data frame, I choose edible/poisonous, cap-shape, cap-surface, cap-color and odor.

mushrooms1 <- mushrooms[ ,1:4]
mushrooms2 <- mushrooms[,6]
mroom <- cbind(mushrooms1, mushrooms2)
head(mroom)
```

    ##   V1 V2 V3 V4 mushrooms2
    ## 1  p  x  s  n          p
    ## 2  e  x  s  y          a
    ## 3  e  b  s  w          l
    ## 4  p  x  y  w          p
    ## 5  e  x  s  g          n
    ## 6  e  x  y  y          a

``` r
colnames(mroom) <- c("Edible/Poisonous", "cap_shape", "cap_surface", "cap_color", "odor")
head(mroom)
```

    ##   Edible/Poisonous cap_shape cap_surface cap_color odor
    ## 1                p         x           s         n    p
    ## 2                e         x           s         y    a
    ## 3                e         b           s         w    l
    ## 4                p         x           y         w    p
    ## 5                e         x           s         g    n
    ## 6                e         x           y         y    a

``` r
#Replacing abbreviation

#Edible/ poisonous
levels(mroom$'Edible/Poisonous') <- c(levels(mroom$'Edible/Poisonous'), c("Edible", "Poisonous"))
mroom$'Edible/Poisonous'[mroom$'Edible/Poisonous'=="e"] <- "Edible"
mroom$'Edible/Poisonous'[mroom$'Edible/Poisonous'=="p"] <- "Poisonous"
# try it out
head(mroom)
```

    ##   Edible/Poisonous cap_shape cap_surface cap_color odor
    ## 1        Poisonous         x           s         n    p
    ## 2           Edible         x           s         y    a
    ## 3           Edible         b           s         w    l
    ## 4        Poisonous         x           y         w    p
    ## 5           Edible         x           s         g    n
    ## 6           Edible         x           y         y    a

``` r
#cap_shape
levels(mroom$'cap_shape') <- c(levels(mroom$'cap_shape'), c("bell", "conical","convex","flat","knobbed","sunken"))
mroom$'cap_shape'[mroom$'cap_shape'=="b"] <-"bell"
mroom$'cap_shape'[mroom$'cap_shape'=="c"] <-"conical"
mroom$'cap_shape'[mroom$'cap_shape'=="x"] <-"convex"
mroom$'cap_shape'[mroom$'cap_shape'=="f"] <-"flat"
mroom$'cap_shape'[mroom$'cap_shape'=="k"] <-"knobbed"
mroom$'cap_shape'[mroom$'cap_shape'=="s"] <-"sunken"


#cap_surface
levels(mroom$'cap_surface') <- c(levels(mroom$'cap_surface'), c("fribrous", "grooves","scaly","smooth"))
mroom$'cap_surface'[mroom$'cap_surface'=="f"] <- "fibrous"
```

    ## Warning in `[<-.factor`(`*tmp*`, mroom$cap_surface == "f", value =
    ## structure(c(3L, : invalid factor level, NA generated

``` r
mroom$'cap_surface'[mroom$'cap_surface'=="g"] <- "grooves"
mroom$'cap_surface'[mroom$'cap_surface'=="y"] <- "scaly"
mroom$'cap_surface'[mroom$'cap_surface'=="s"] <- "smooth"


#cap_color
levels(mroom$'cap_color') <- c(levels(mroom$'cap_color'), c("brown","buff","cinnamon", "gray", "green", "pink", "purple", "red","white","yellow"))
mroom$'cap_color'[mroom$'cap_color'=="n"]<- "brown"
mroom$'cap_color'[mroom$'cap_color'=="b"]<- "buff"
mroom$'cap_color'[mroom$'cap_color'=="c"]<- "cinnamon"
mroom$'cap_color'[mroom$'cap_color'=="g"]<- "gray"
mroom$'cap_color'[mroom$'cap_color'=="r"]<- "green"
mroom$'cap_color'[mroom$'cap_color'=="p"]<- "pink"
mroom$'cap_color'[mroom$'cap_color'=="u"]<- "purple"
mroom$'cap_color'[mroom$'cap_color'=="e"]<- "red"
mroom$'cap_color'[mroom$'cap_color'=="w"]<- "white"
mroom$'cap_color'[mroom$'cap_color'=="y"]<- "yellow"

levels(mroom$'odor') <- c(levels(mroom$'odor'), c("almond", "anise","creosote", "fishy", "foul", "musty", "none", "pungent","spicy"))
mroom$'odor' [mroom$'odor'=="a"] <- "almond"
mroom$'odor' [mroom$'odor'=="l"] <- "anise"
mroom$'odor' [mroom$'odor'=="c"] <- "creosote"
mroom$'odor' [mroom$'odor'=="y"] <- "fishy"
mroom$'odor' [mroom$'odor'=="f"] <- "foul"
mroom$'odor' [mroom$'odor'=="m"] <- "musty"
mroom$'odor' [mroom$'odor'=="n"] <- "none"
mroom$'odor' [mroom$'odor'=="p"] <- "pungent"
mroom$'odor' [mroom$'odor'=="s"] <- "spicy"

head(mroom)
```

    ##   Edible/Poisonous cap_shape cap_surface cap_color    odor
    ## 1        Poisonous    convex      smooth     brown pungent
    ## 2           Edible    convex      smooth    yellow  almond
    ## 3           Edible      bell      smooth     white   anise
    ## 4        Poisonous    convex       scaly     white pungent
    ## 5           Edible    convex      smooth      gray    none
    ## 6           Edible    convex       scaly    yellow  almond
