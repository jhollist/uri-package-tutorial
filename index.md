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

<img src="http://imgs.xkcd.com/comics/packages.png" style="position: absolute; width:600px; bottom: 50px;left:300px; right:300px;"/>

--- &twocol w1:40% w2:60%

## Base and Recommended

***=left
- base (14 Packages)
- recommended (15 Packages)
- First few

***=right


|          |LibPath                            |Priority    |
|:---------|:----------------------------------|:-----------|
|base      |C:/Program Files/R/R-3.1.1/library |base        |
|boot      |C:/Program Files/R/R-3.1.1/library |recommended |
|class     |C:/Program Files/R/R-3.1.1/library |recommended |
|cluster   |C:/Program Files/R/R-3.1.1/library |recommended |
|codetools |C:/Program Files/R/R-3.1.1/library |recommended |
|compiler  |C:/Program Files/R/R-3.1.1/library |base        |
|datasets  |C:/Program Files/R/R-3.1.1/library |base        |
|foreign   |C:/Program Files/R/R-3.1.1/library |recommended |


--- &twocol w1:35% w2:60%

## Finding New Packages

***=left
- My own rule of thumb:  If you can think it, you can do it R
- Chances are, someone else has done so already
- For comparison
 - SAS ~1200 proc's
 - R ~153,696 functions
 
***=right
<img src="http://r4stats.files.wordpress.com/2012/04/fig_8_cran.png" style="width: 500px; bottom: 50px;"/>

--- 

## Finding New Packages

- Source Repositories
 - CRAN ([http://cran.r-project.org/](http://cran.r-project.org/))
 - RForge ([https://r-forge.r-project.org/](https://r-forge.r-project.org/))
 - BioConductor ([http://www.bioconductor.org/](http://www.bioconductor.org/))
 - GitHub ([https://github.com/](https://github.com/search?l=R&q=R&type=Repositories&utf8=%E2%9C%93))

--- 
## Finding New Packages

- Finding Packages and Getting Help
 - CRAN Task Views ([http://cran.r-project.org/web/views/](http://cran.r-project.org/web/views/))
 - StackOverflow ([http://stackoverflow.com/questions/tagged/r](http://stackoverflow.com/questions/tagged/r))
 - Journal of Statistical Software ([http://www.jstatsoft.org/](http://www.jstatsoft.org/))
 - R Journal ([http://journal.r-project.org/](http://journal.r-project.org/))
 - Twitter, #rstats ([https://twitter.com/](https://twitter.com/search?q=%23rstats))
 - R Bloggers ([http://www.r-bloggers.com/](http://www.r-bloggers.com/))

--- 

## Managing Packages
- listing: `installed.packages()`
- available from current repository: `available.packages()`
- install: `install.packages()`
- remove: `remove.packages()`
- update: `update.packages()`
- loading: `library()` 
 - note: see [Yihui Xie's post](http://yihui.name/en/2014/07/library-vs-require/) on `library` not `require`
- help: `help(package="package_name")`

---

## Live Coding - Typical workflow

1. Find
2. Install
3. Load
4. Explore

## Excercise
Using one of the provided links above, find a package, install it, load it, and get to the help page for that package

---

## Anatomy of a function

<h3>function_name(param1, param2, param3=NULL)</h3>

<h3>Aside on style (my opinion)</h3>
- snake_case (good)
- camelCase (fair)
- UpperCamelCase (fair)
- alllowercase (good)
- period.separated (poor)
- consistent (best)
- inconsistent (BAD!!!!)

For more, [R Journal](http://journal.r-project.org/archive/2012-2/RJournal_2012-2_Baaaath.pdf)

--- 

## A few examples



```r
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

--- &twocol w1:27% w2:73%

## A few examples

***=left

```r
args(t.test)
```

```
## function (x, ...) 
## NULL
```

***=right

```r
t.test(rnorm(100),rnorm(100,10,1),mu=0)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  rnorm(100) and rnorm(100, 10, 1)
## t = -69.68, df = 196.8, p-value < 2.2e-16
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -10.481  -9.904
## sample estimates:
## mean of x mean of y 
##   -0.1874   10.0051
```

---

## Writing your own functions

The `function()` function...


```r
#Create it
my_function<-function(txt_to_print){
  print(txt_to_print)
}
#Now Use It
my_function("Hello World!!")
```

```
## [1] "Hello World!!"
```

---
## Live Coding & Excercise - linear model

1. Create some data
2. Look at help for `lm()`
3. Try `summary()` to get more info out of your `lm()`

## Excercise
Write a function that has two vectors of the same length as input, and returns 
the R<sup>2</sup> of the linear regression between the two.  Use the code below as a starting
place


```r
#Replace ... with your code.  Does not imply that all ... code is the same!
get_r2<-function(...){
  xlm<-lm(...)
  xlm_summary<-summary(...)
  return(...) # hint str(xlm_summary) will give you lots of useful info
}
```

--- &twocol w1:40% w2:50%

## Creating your own packages

***=left
- Why?
 - You have developed a new method
 - Share code for a published paper
 - Keep your own code organized
 
> - When?
 - A method is finalized
 - Paper is published
 - Anytime you have more than one related function
> - How?

***=right
![Steve Package](http://media.giphy.com/media/9xfrrhLlYOeNq/giphy.gif)

---

## How do you create your own package?

- Many tutorials out there
 - Hadley Wickham - [http://r-pkgs.had.co.nz/](http://r-pkgs.had.co.nz/)
 - Hilary Parker - [http://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/](http://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/)
 - Karl Broman - [http://kbroman.org/pkg_primer/](http://kbroman.org/pkg_primer/)
 
- But, the very basics are
 - Structure
 - Documentation
 - `DESCRIPTION` File

--- &twocol w1:34% w2:66%

## Create the Structure

***=left
- `package.skeleton()`
- `devtools::create()`
- RStudio project

***=right

```r
devtools::create("test")
```

```
## Creating package test in .
```

```
## Error: Directory already exists
```

```r
list.files("test")
```

```
## [1] "DESCRIPTION" "man"         "R"
```

--- &twocol w1:40% w2:58%%

## Create the Documentation

***=left
- Edit `.Rd` directly
- `roxygen2`
 - `roxygen2::roxygenize()`
 - `devtools::document()`
 - RStudio

***=right

```r
#' Get r2
#'
#' This function takes two input vectors,
#' runs a linear regression and returns 
#' the coeffecient of determination.
#'
#' @param x The independent variable
#' @param y The dependent variable
#' @export
get_r2<-function(x,y){
  xlm<-lm(y~x)
  xlm_summary<-summary(xlm)
  return(xlm_summary$r.squared) 
}
```

--- &twocol w1:42% w2:55%
 
## Fill out DESCRIPTION

***=left
- Edit directly
- `devtools::create_description()`

***=right
```
Package: test
Title: What the package does (short line)
Version: 0.1
Authors@R: "First Last <first.last@example.com> 
            [aut, cre]"
Description: What the package does (paragraph)
Depends: R (>= 3.1.1)
License: What license is it under?
LazyData: true
```

---

## Build the package

- Won't work in lab (maybe on mac side)
- Command line
 - `R CMD build`
 - `R CMD check`
- `devtools::build()`
- RStudio
- devtools

## Share it with the world

- CRAN ([http://cran.r-project.org/submit.html](http://cran.r-project.org/submit.html))
- GitHub (i.e. [https://github.com/jhollist](https://github.com/jhollist))
