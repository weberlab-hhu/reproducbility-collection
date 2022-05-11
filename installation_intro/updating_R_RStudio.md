# Updating R (and RStudio)

## Prep

1. Close RStudio
2. Make sure you are not running R or an R script in a command line

## Download and install R and Rstudio

1. R: Go to https://www.r-project.org/ and follow the instructions for your OS to install the latest version of R
2. RStudio: Got to https://www.rstudio.com/ and  follow the instructions for your OS to install the latest version of RStudio Desktop (Free)
  - Alternatively: Within RStudio click "Help -> Check For Updates" and follow instructions

## Caveats

- Some libraries do not work with newer versions
- Migrating package dependencies ("libraries") from one R version to the next is not straight forward
- If you want to know, where R libraries are stored on your system, you can do this within R via `.libPaths`, e.g.

```r
.libPaths()
[1] "/Library/Frameworks/R.framework/Versions/4.2/Resources/library"
```

- Accordingly, you would find libraries installed with earlier versions (in this case `3.6`) via command line in e.g.:

```bash
ls -l /Library/Frameworks/R.framework/Versions/3.6/Resources/library
```

## Recommendations

Rather than trying to migrate (copy over) possibly outdated packages between versions, I'd recommend to re-install them freshly as needed.
This also has the benefit that many dependencies (other packages) are oftentimes likely updated in the same go.

### Installing a standard R package (from CRAN)

Usually we load a package to use it with the current script via the `library` command.
After upgrading to a new R version, this command will not find a library (e.g. "tidyverse") installed with the previous version.

```r
library(tidyverse)
Error in library(tidyverse) : there is no package called ‘tidyverse’
```

Standard libraries listed at CRAN can easily be installed with `install.packages`:

```r
install.packages("tidyverse")
```

### Installing from bioconductor

Bioconductor is a famous package manager for bioinformatics tools, mostly focusing on R.
The package installation routine changed in the past, so make sure to google and / or check https://www.bioconductor.org/, if things might have changed.

- To install core packages, type the following in an R command window:

```r
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install()
```

- Install specific packages, e.g., “GenomicFeatures” and “AnnotationDbi”, with

```r
BiocManager::install(c("GenomicFeatures", "AnnotationDbi"))
```

### Package versions

#### Document

To avoid crashing code due to (unclear) package dependencies, it's a good habit to simply log the installed (and loaded) packages incl. their version via the `sessionInfo()`, e.g. by printing at the end of your RMarkdown file.

```r
sessionInfo()

R version 4.2.0 (2022-04-22)
Platform: x86_64-apple-darwin17.0 (64-bit)
Running under: macOS Monterey 12.3.1

Matrix products: default
LAPACK: /Library/Frameworks/R.framework/Versions/4.2/Resources/lib/libRlapack.dylib

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] BiocManager_1.30.17
```

In addition to the package dependencies, it also prints the current versions of R and your OS, which is always good to have for asking questions (e.g. stackoverflow). 

### Adapt your code to automatically install packages if required

Most basic R scripts (no matter if *.Rmarkdown or *.R), start with a simple block loading all dependent packages via `library`.
By just adding an additional line above that checks wether the package is installed (or "required"), you can make sure that whoever uses the script (colleagues or your future self after a fresh install) installs the package first.

```r
if (!require("Rmisc", quietly = TRUE)){install.packages("Rmisc")}
library(Rmisc)
```

### Install specific versions

If you run into an R script, where you need a specific (possibly deprecated) package version (e.g. based on somebody's [`sessionInfo`](#document)), there are options. 

The simplest way is via devtools: 

```r
if (!require("devtools", quietly = TRUE)){install.packages("devtools")}
library(devtools)
install_version("ggplot2", version = "0.9.1")
```
