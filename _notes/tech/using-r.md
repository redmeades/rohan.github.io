---
title: Notes on using R
layout: tech
---

See my [Guide to R]({% link _guides/r-for-data-analysis-reporting.md %}) for more use oriented notes.

### Installing dev versions of packages

Sometimes code changes introduce issues that get quickly fixed in versions but
are not yet made available through regular channels. R has a mechanism to
install packages directly from github or gitlab.

A real example was from when Homebrew's R went from 3.5 to 3.6 and lwgeom failed to
install as a dependency proj also was upgraded (v6.0). I installed the dev
version of lwgeom with:

```
library(devtools)
install_github("r-spatial/lwgeom")
```

You can (because you may need to) build packages from source and supply
additional configuration (here using paths that Homebrew would use):

```
install.packages('rgdal', type = "source", configure.args=c('--with-proj-include=/usr/local/include','--with-proj-lib=/usr/local/lib'))

```
### Less painful upgrades

You can [see what has been
installed](https://shiny.rstudio.com/articles/upgrade-R.html) and what version
the package was built with.

```
installed.packages()

# build versions
pkgs <- as.data.frame(installed.packages(), stringsAsFactors = FALSE, row.names = FALSE)
pkgs[, c("Package", "Version", "Built")]
```
Cribbing various parts from [this
post](https://github.com/lmmx/devnotes/wiki/Updating-R-on-Linux) led to the
following way to deal with upgrading R on a Mac, installed via Homebrew

```{lang=r}
# get list of package from old library, massage into list
tmp.pkg.list <- installed.packages(lib.loc = "~/Library/R/3.5/library")
installedpackages <- as.vector(tmp.pkg.list[is.na(tmp.pkg.list[,"Priority"]), 1])

# install list of packages
for (count in 1:length(installedpackages)) install.packages(installedpackages[count])
```


## links to get cetain things working

* [Arrange by variable not facet](https://dplyr.tidyverse.org/reference/arrange.html)
* and <https://stackoverflow.com/questions/5208679/order-bars-in-ggplot2-bar-graph>
* and <https://rstudio-pubs-static.s3.amazonaws.com/7433_4537ea5073dc4162950abb715f513469.html>
* and <https://www.r-bloggers.com/how-do-i-re-arrange-ordering-a-plot-revisited/>
* Plotting [Cumulative Data](https://ggplot2.tidyverse.org/reference/stat_ecdf.html)
* [and](https://stats.stackexchange.com/questions/30858/how-to-calculate-cumulative-distribution-in-r)
* [and a function](https://statisticsglobe.com/cumsum-r-function-explained/)
* Barplots [Data to Viz](https://www.data-to-viz.com/graph/barplot.html)
* And [R Graph gallery](https://www.r-graph-gallery.com/barplot.html)
* and [more](https://ggplot2.tidyverse.org/reference/geom_boxplot.html)
* and [further](https://ggplot2.tidyverse.org/reference/geom_bar.html)
* and <https://www.statmethods.net/graphs/bar.html>
* [advanced graphs](https://www.statmethods.net/advgraphs/index.html)
* colour [palettes](https://www.datanovia.com/en/blog/the-a-z-of-rcolorbrewer-palette/)
* and expanding it beyond the [small default](https://www.r-bloggers.com/how-to-expand-color-palette-with-ggplot-and-rcolorbrewer/)
* often one wants [interquartile ranges](http://www.r-tutor.com/elementary-statistics/numerical-measures/interquartile-range)
* and [this](https://statisticsglobe.com/quantile-function-in-r-example)
