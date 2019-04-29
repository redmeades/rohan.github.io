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
