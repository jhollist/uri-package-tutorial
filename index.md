---
title       : Packages and functions in R
subtitle    : 10/26/2014
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

--- &twocol w1:40% w2:60%

## What are Packages


> An extension of the R base system with code, data and documentation in standardized
format.[1](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf)

<img src="http://imgs.xkcd.com/comics/packages.png" style="position: absolute; width:500px; bottom: 50px;left:300px; right:300px;"/>

--- &twocol w1:40% w2:60%

## Base and Recommended

***=left
- base (14 Packages)
- recommended (15 Packages)

***=right


|           |LibPath                            |Priority    |
|:----------|:----------------------------------|:-----------|
|base       |C:/Program Files/R/R-3.1.1/library |base        |
|boot       |C:/Program Files/R/R-3.1.1/library |recommended |
|class      |C:/Program Files/R/R-3.1.1/library |recommended |
|cluster    |C:/Program Files/R/R-3.1.1/library |recommended |
|codetools  |C:/Program Files/R/R-3.1.1/library |recommended |
|compiler   |C:/Program Files/R/R-3.1.1/library |base        |
|datasets   |C:/Program Files/R/R-3.1.1/library |base        |
|foreign    |C:/Program Files/R/R-3.1.1/library |recommended |
|graphics   |C:/Program Files/R/R-3.1.1/library |base        |
|grDevices  |C:/Program Files/R/R-3.1.1/library |base        |
|grid       |C:/Program Files/R/R-3.1.1/library |base        |
|KernSmooth |C:/Program Files/R/R-3.1.1/library |recommended |

--- 

## Managing Packages


- listing: `installed.packages()`
- available from current repository: `available.packages()`
- install: `install.packages()`
- remove: `remove.packages()`
- update: `update.packages()`
- loading: `library()` 
 - note: see [Yihui Xie's post](http://yihui.name/en/2014/07/library-vs-require/) on `library` not `require`

---

## Finding New Packages

- My own rule of thumb:  If you can think it, you can do it R
- Chances are, someone else has done so already



---

## Finding New Packages

***=left
- Source Repositories
 - CRAN
 - RForge
 - BioConductor
 - GitHub
 
***=right
- Getting Help
 - CRAN Task Views
 - SourceForge
 - Journal of Statistical Software
 - R Journal
 - Twitter (#rstats, @RLangTip)
 - R Bloggers
 
---

## Live Coding: Typical workflow

---

## Anatomy of a function

###function_name(param1, param2, param3=NULL)

###Aside on style (my opinion)
- snake_case (good)
- camelCase (fair)
- UpperCamelCase (fair)
- alllowercase (good)
- period.separated (poor)
- For more, [R Journal](http://journal.r-project.org/archive/2012-2/RJournal_2012-2_Baaaath.pdf)
- consistent (best)
- inconsistent (BAD!!!!)

--- &twocol w1:40% w2:60%

## A few examples


```r
#Median
args(median)
```

```
## function (x, na.rm = FALSE) 
## NULL
```

```r
median(1:100)
```

```
## [1] 50.5
```

```r
#t.test
args(t.test)
```

```
## function (x, ...) 
## NULL
```

```r
t.test(rnorm(100),rnorm(100,10,1),mu=0)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  rnorm(100) and rnorm(100, 10, 1)
## t = -69.6, df = 198, p-value < 2.2e-16
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -10.47  -9.89
## sample estimates:
## mean of x mean of y 
##  -0.04242  10.13559
```

