---
Date: 2022-02-05
Author: Jimmy Briggs <jimmy.briggs@jimbrig.com>
Tags: ["#Type/Tool/R/RPackage", "#Topic/Dev/R", "#Type/Tool", "#Topic/Dev/Data/Databases"]
Alias: ["R Package - DBconnectR", "DBconnectR"]
---

# R Package - DBconnectR

*Source: [ekoepplin/DBconnectR: R client to query data from different sources (github.com)](https://github.com/ekoepplin/DBconnectR)*

## Overview

_R client to query data from different sources_

The following functions are implemented:

-   `run_query.R`: runs quries agains different databases

## Installation

- Stable Version:

```R
# install package from CRAN
install.packages("DBconnectR")
# load package
library(DBconnectR)
```

- Development Version

```R
# install devtools package if it's not already
if (!requireNamespace("devtools", quietly = TRUE)) {
install.packages("devtools")
}
# install package from GitHub
devtools::install_github("ekoepplin/DBconnectR")
# load package
library(DBconnectR)
```

***

## Appendix: Links

- [[Tools]]
- [[Development]]
- [[R]]
- [[R Database Packages]]


*Backlinks:*

```dataview
list from [[R Package - DBconnectR]] AND -"Changelog"
```