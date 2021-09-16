# errorReprex
reproducible example of an R package install error

the command ```R CMD INSTALL errorReprex``` fails in the error branch. Error message displayed below.
In the `no_error` branch there is no failure.  The only difference between the two branches is the presence of
`import(emayili)` in the `NAMESPACE` file in the error branch.

Also neither branch fails if the package version of emayili is <= 0.4.15

Steps to reproduce

### Setup

[optional run on docker image] `docker run -it rocker/tidyverse bash`

`git clone https://github.com/adam-gruer/errorReprex.git`

`Rscript -e 'install.packages("emayili")'`

### Error
`R CMD INSTALL errorReprex`

### No error

`cd errorReprex`

`git checkout no_error`

`cd ..`

`R CMD INSTALL errorReprex`


## Error output

```sh
* installing to library ‘/usr/local/lib/R/site-library’
* installing *source* package ‘errorReprex’ ...
** using staged installation
** R
** byte-compile and prepare package for lazy loading
** help
No man pages found in package  ‘errorReprex’
*** installing help indices
** building package indices
** testing if installed package can be loaded from temporary location
Error : Can't convert <logical> to <character>.
Error: package or namespace load failed for ‘errorReprex’:
 unable to load R code in package ‘errorReprex’
Error: loading failed
Execution halted
ERROR: loading failed
* removing ‘/usr/local/lib/R/site-library/errorReprex’

```
