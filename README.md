# dataCompareR

dataCompareR is an R package that allows users to compare two datasets and view a report on the similarities and differences. 

dataCompareR aims to make it easy to compare two tabular data objects in R. It’s specifically designed to show differences between two sets of data in a useful way that should make it easier to understand the differences, and if necessary, help you work out how to remedy them. In this regard, it aims to offer a more useful output than *all.equal* when your two datasets do not match, but isn’t intended to replace *all.equal* if you just want to test for equality.

[![](http://cranlogs.r-pkg.org/badges/datacompareR)](http://cran.rstudio.com/web/packages/datacompareR/index.html)

## Getting started

### Installing the package

We intend to submit dataCompareR to the CRAN in the near future. In the meantime, you can install directly from GitHub via


```{r}
library(devtools)
install_git('https://github.com/capitalone/dataCompareR.git', branch = 'master',
            subdir = 'dataCompareR', type = 'source', repos = NULL)
```
    
Alternatively, if this fails, download and extract the package on the same machine you're running R and then run


```{r}
library(devtools)
install_local('/pathtodataCompareR/dataCompareR', type = 'source', repos=NULL)
```

Replacing /pathtodataCompareR with the path you downloaded the package to.

### Using dataCompareR

Please run `vignette('dataCompareR')` after installation to see an example of the dataCompareR workflow.

### Requirements

Confirmed as working on R v3.2.3 and later on Linux/Windows, both via RStudio and through the command line.
Package was built with the following dependencies, but we anticipate it will work with later versions of these packages.

| Package|Version|Source code URL|
| ---|---|--- |
|dplyr|	0.5.0|	https://github.com/hadley/dplyr |
|knitr|	1.12.3|	https://github.com/yihui/knitr |
|stringi|	1.0-1|	https://github.com/gagolews/stringi |
|markdown|0.7.7|	https://github.com/rstudio/markdown |


### Repo Contents 

The code is arranged as an R package, with the following contents:

- dataCompareR/R
- dataCompareR/man
- dataCompareR/tests/testthat
- dataCompareR/tests/performancetesting
- dataCompareR/inst/css
- dataCompareR/vignette

The contents will be covered below.

#### dataCompareR/R

The main body of R code that provide the dataCompareR functionality.

The R package format mandates that this is a flat folder structure. Initial development had a nested structure, so to try to maintain this as far as possible, the naming convention for files is to preface them with 2 or 3 letter code that identifies the part of the code that file belongs to. The codes and hierarchy is as follows

- rc - rCompare - the entry point of the function
    - pf - processFlow - handles the flow of an rCompare run
        - vd - validateData - checks the data is suitable before starting an rCompare run
        - pd - prepareData - prepares the input data for comparison
        - cd - compareData - does the comparison
    - rco - rCompare object - routines to handle the rCompare object that is generated by an rCompare run
    - out - output - code to provide various views of the output

The filenames follow the format of the prefix, followed by underscore, followed by a camelcase description of what the code does. The .R files tend to have either 1 function inside them, or a small number of related functions.

#### dataCompareR/man 

Code is commented using ROxygen2 headers, which is used to automatically create the required R man pages by running

``devtools::document()``

#### dataCompareR/tests/testthat

Automated tests that are run via

``devtools::test()``

This consists of both unit tests and some end-to-end tests that **MUST** pass before any code is merged to dev or main. There is no exception to this - if your code change breaks an existing test, then it is your responsibility to fix it! 

The current unit test coverage can be founbd in `testing.md` -  please feel free to add more tests!

#### dataCompareR/tests/performancetesting

This folder contains useful repeatable performance tests, but there are not run automatically, and the results they produce can only be interpreted manually.

## CRAN Release Version History

https://cran.r-project.org/package=dataCompareR

Version 0.1.0 released on 2017-07-17

## External Contributors

Contributors: We welcome your interest in Capital One’s Open Source Projects (the “Project”). 

Any Contributor to the project must accept and sign a CLA indicating agreement to the license terms. Except for the license granted in this CLA to Capital One and to recipients of software distributed by Capital One, you reserve all right, title, and interest in and to your contributions; this CLA does not impact your rights to use your own contributions for any other purpose. 

[Link to Individual CLA](https://docs.google.com/forms/d/19LpBBjykHPox18vrZvBbZUcK6gQTj7qv1O5hCduAZFU/viewform)

[Link to Corporate CLA ](https://docs.google.com/forms/d/e/1FAIpQLSeAbobIPLCVZD_ccgtMWBDAcN68oqbAJBQyDTSAQ1AkYuCp_g/viewform)

This project adheres to the [Open Source Code of Conduct](https://developer.capitalone.com/single/code-of-conduct/). By participating, you are expected to honor this code. 
