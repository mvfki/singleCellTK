# Single Cell TK

[![Travis build status](https://travis-ci.org/compbiomed/singleCellTK.svg?branch=master)](https://travis-ci.org/compbiomed/singleCellTK)
[![codecov](https://codecov.io/gh/compbiomed/singleCellTK/branch/master/graph/badge.svg)](https://codecov.io/gh/compbiomed/singleCellTK)
[![BioC status](https://www.bioconductor.org/shields/build/release/bioc/singleCellTK.svg)](https://bioconductor.org/checkResults/release/bioc-LATEST/singleCellTK)
[![lifecycle](https://img.shields.io/badge/lifecycle-stable-brightgreen.svg)](https://www.tidyverse.org/lifecycle/#stable)


The Single Cell ToolKit (SCTK) is an analysis platform that provides an <b> R interface to 
several popular scRNA-seq preprocessing, quality control, and visualization tools</b>. SCTK imports
raw or filtered counts from various single cell sequencing technologies 
and upstream tools such as 10x CellRanger, BUStools, Optimus, STARSolo, and more. By integrating several publicly available tools written in R as well as Python, SCTK performs extensive quality control measures including doublet detection and batch effect correction. Additionally, SCTK summarizes results and related visualizations in a comprehensive R markdown and/or HTML report. SCTK provides a standardized single cell analysis workflow by representing the counts data and the results using the [SingleCellExperiment](https://www.bioconductor.org/packages/release/bioc/html/SingleCellExperiment.html) R object. Furthermore, SCTK enables seamless downstream analysis by exporting data and results in flat .txt and Python Anndata formats.

A comprehensive list of available functions is listed in the Reference section

## Installation

### System setup

If you are the first time to install R, please don't install 32 bit R. Make sure to uncheck the '32-bit Files' box when you see the following window:

![](32bit-R.png)

#### Window's user
For window's users, please install [rtools](https://cran.r-project.org/bin/windows/Rtools/history.html) based on your R version. Make sure to click 'Edit the system PATH' box when you see this window:

![](rtools.png)

After installing rtools, install 'devtools' package with the following command. If it asks whether install the package that requires compilation, type 'y'. 
```
install.packages('devtools')
```

#### macOS user
For macbook's users, please install gfortran with brew. If you have not installed brew, please check [this link](https://brew.sh/) to set up brew on your machine. 
```
brew install gcc
```

After that, install 'devtools' package with the following command.
```
install.packages('devtools')
```

### Release Version

The current release version of SCTK can be downloaded from
[Bioconductor v3.10](https://bioconductor.org/packages/release/bioc/html/singleCellTK.html):

```r
if (!requireNamespace("BiocManager", quietly=TRUE))
  install.packages("BiocManager")
BiocManager::install("singleCellTK")
```

Load the package for analysis by running

```r 
library(singleCellTK)
```

### Development Version

The development version is available at
[Bioconductor v3.11](https://bioconductor.org/packages/devel/bioc/html/singleCellTK.html)
or from this repository:

```r
# install.packages("devtools")
devtools::install_github("compbiomed/singleCellTK",ref="devel")
```

### Install From Containerized Images

singleCellTK is available for use with both Docker and Singularity.

#### Docker

Docker set up instructions are available at - [Windows](https://docs.docker.com/docker-for-windows/), [Mac](https://docs.docker.com/docker-for-mac/) or [Linux](https://runnable.com/docker/install-docker-on-linux).

SingleCellTK docker image is available at [Docker Hub](https://hub.docker.com/r/campbio/sctk_qc).

The Docker image can be obtained by running:

```
docker pull campbio/sctk_qc
```


#### Singularity

The Singulatiry image sources the docker image and can be obtained as follows- 

```
singularity pull docker://campbio/sctk_qc:1.7.5
```

#### Troubleshooting R Installation

For the majority of users, the commands above will install the latest version
of the singleCellTK without any errors. Rarely, you may encounter an error due
to previously installed versions of some packages that are required for the
singleCellTK. If you encounter an error during installation, use the commands
below to check the version of Bioconductor that is installed:

```r
if (!requireNamespace("BiocManager", quietly=TRUE))
    install.packages("BiocManager")
BiocManager::version()
```

If the version number is not 3.6 or higher, you must upgrade Bioconductor to
install the toolkit:

```r
BiocManager::install()
```

After you install Bioconductor 3.6 or higher, you should be able to install the
toolkit using `devtools::install_github("compbiomed/singleCellTK")`. If you
still encounter an error, ensure your Bioconductor packages are up to date by
running the following command.

```r
BiocManager::valid()
```

If the command above does not return `TRUE`, run the following command to
update your R packages:

```r
BiocManager::install()
```

Then, try to install the toolkit again:

```r
devtools::install_github("compbiomed/singleCellTK")
```

If you still encounter an error, please [contact us](mailto:camp@bu.edu) and
we'd be happy to help.

## Develop singleCellTK

To contribute to singleCellTK, follow these steps:

__Note__: Development of the singleCellTK is done using R version 3.6.

1. Fork the repo using the "Fork" button above.
2. Download a local copy of your forked repository "```git clone https://github.com/{username}/singleCellTK.git```"
3. Open Rstudio
4. Go to "File" -> "New Project" -> "Existing Directory" and select your git repository directory

You can then make your changes and test your code using the Rstudio build tools.
There is a lot of information about building packages available here: http://r-pkgs.had.co.nz/.
When you are ready to upload your changes, commit them locally, push them to your
forked repo, and make a pull request to the compbiomed repository.

Report bugs and request features on our [GitHub issue tracker](https://github.com/compbiomed/singleCellTK/issues).

Join us on [slack](https://compbiomed.slack.com/)!
