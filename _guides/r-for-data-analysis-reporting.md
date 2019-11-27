---
title: Using R for data, analysis and reporting
layout: guide
permalink: /guides/using-r/
date: 2019-11-27
---

I have been using R for a while to analyse data sets at the University and write
up reports from these. My typical workflow is to use Rmarkdown and Knitr to do this.

My basic template for knitr has the following chunk after the YAML header
(excluding backticks) that loads up :

```
{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
#
------------------------------------------------------------------------------------------------
libs <- c("tidyr", "dplyr", "readr", "tibble", "knitr", "ggplot2","lubridate","stringi","purrr","RPostgres")
lapply(libs, library, character.only = TRUE)```
```

### Loading data

Typically, one loads up data from files exported from other systems. These are
often in CSV format, but R can also handle Excel documents and a wide variety of
files. I usually place by input data in a sub-folder data/.

```
units <- read_csv(paste0('data/','sru-enrolment-counts','.csv'))  #, col_types = "dcccccdcccc")
```

Rather than loading via CSV, R [supports database
connections](https://db.rstudio.com/getting-started/database-queries) and querying in a
similar fashion to other programming languages.

And further, knitre chunks can actually contain SQL code that uses a previously established
connection, in this case one via RPostgres, and stores the result in the
variable specified.

```
{sql, connection=con, output.var="units_df"}
SELECT units.id, code,
```

### Manipulating data

I often turn to [the Tidyverse](https://tidyverse.org/) for the tools that I use
for this step.


### Quartiles and Distributions

R has a **quantile**
[funtion](https://www.rdocumentation.org/packages/stats/versions/3.6.1/topics/quantile)
thatdefaults to quartiles, but can [do deciles, percentils and
more](https://www.r-bloggers.com/quartiles-deciles-and-percentiles/). See [some
examples](https://statisticsglobe.com/quantile-function-in-r-example) that 

* https://www.statisticshowto.datasciencecentral.com/cumulative-distribution-function/

### Outputs

Another part of the Tidyverse that I frequently utilise is
[ggplot](https://ggplot2.tidyverse.org/). Once you begin dealing with complex
data you need to think through the visualisation aspects and [from Data to
Viz](http://www.data-to-viz.com/) is an excellent resource.

I sometimes have multiple factors that require plotting concurrently which
creates an issue for colouring. You can adjust the adjust [the colour
palette](https://www.datanovia.com/en/blog/the-a-z-of-rcolorbrewer-palette/) and
the [number of colours
available](https://www.r-bloggers.com/how-to-expand-color-palette-with-ggplot-and-rcolorbrewer/)

### Bigger data

When dealing with larger data sets, long computation times, or
['expensive'](https://stackoverflow.com/questions/3347375/cache-expensive-operations-in-r)
operations (such as a database connection and query) it can be [useful to cache
the results in some
fashion](https://stackoverflow.com/questions/7262485/options-for-caching-memoization-hashing-in-r).
In fact, there is [an online book on Efficient R
programming(https://csgillespie.github.io/efficientR/)

