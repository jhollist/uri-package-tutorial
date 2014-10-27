---
title       : Packages and functions in R
subtitle    : 
author      : Jeff Hollister
logo        : epa-seal.png
biglogo     : epa-seal.png
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## Goals

1. Describe what a package is
2. Know where and how to find and install new packages
3. Know how to manage your packages
4. Know how to work with and build your own functions
5. Know how to manage multiple funcitons and build your own packages

--- &twocol w1:20% w2:80%

## Packages

***=left
- what is a package?

***=right
> An extension of the R base system with code, data and documentation in standardized
format.[1](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf)

--- &twocol w1:20% w2:80%

## Packages

***=left
- base 
- recommended

***=right


```
## 
## 
## |           |LibPath                            |Priority    |
## |:----------|:----------------------------------|:-----------|
## |base       |C:/Program Files/R/R-3.1.1/library |base        |
## |boot       |C:/Program Files/R/R-3.1.1/library |recommended |
## |class      |C:/Program Files/R/R-3.1.1/library |recommended |
## |cluster    |C:/Program Files/R/R-3.1.1/library |recommended |
## |codetools  |C:/Program Files/R/R-3.1.1/library |recommended |
## |compiler   |C:/Program Files/R/R-3.1.1/library |base        |
## |datasets   |C:/Program Files/R/R-3.1.1/library |base        |
## |foreign    |C:/Program Files/R/R-3.1.1/library |recommended |
## |graphics   |C:/Program Files/R/R-3.1.1/library |base        |
## |grDevices  |C:/Program Files/R/R-3.1.1/library |base        |
## |grid       |C:/Program Files/R/R-3.1.1/library |base        |
## |KernSmooth |C:/Program Files/R/R-3.1.1/library |recommended |
## |lattice    |C:/Program Files/R/R-3.1.1/library |recommended |
## |MASS       |C:/Program Files/R/R-3.1.1/library |recommended |
## |Matrix     |C:/Program Files/R/R-3.1.1/library |recommended |
## |methods    |C:/Program Files/R/R-3.1.1/library |base        |
## |mgcv       |C:/Program Files/R/R-3.1.1/library |recommended |
## |nlme       |C:/Program Files/R/R-3.1.1/library |recommended |
## |nnet       |C:/Program Files/R/R-3.1.1/library |recommended |
## |parallel   |C:/Program Files/R/R-3.1.1/library |base        |
## |rpart      |C:/Program Files/R/R-3.1.1/library |recommended |
## |spatial    |C:/Program Files/R/R-3.1.1/library |recommended |
## |splines    |C:/Program Files/R/R-3.1.1/library |base        |
## |stats      |C:/Program Files/R/R-3.1.1/library |base        |
## |stats4     |C:/Program Files/R/R-3.1.1/library |base        |
## |survival   |C:/Program Files/R/R-3.1.1/library |recommended |
## |tcltk      |C:/Program Files/R/R-3.1.1/library |base        |
## |tools      |C:/Program Files/R/R-3.1.1/library |base        |
## |utils      |C:/Program Files/R/R-3.1.1/library |base        |
```


## Header Across The Full Width of Both of the Columns

***=left

- list
- on the left 
- side

***=right

Table       |Table        |Table      |Table           |
------------|-------------|-----------|----------------|
First Row   | 1234567     |0.82       |5.95            |
Second Row  | 89          |0.69       |5.02            |
Third Row   | 100         |0.72       |7.0             |

--- &twocol w1:50% w2:50%

## R Code Chunk Example

***=left
Some data and a plot:


```r
data(mtcars)
with(mtcars,boxplot(mpg~factor(cyl)))
```

***=right
![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3.png) 
