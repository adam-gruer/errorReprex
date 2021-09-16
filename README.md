# errorReprex
reproducible example of an R package install error

the command ```R CMD INSTALL errorReprex``` fails in the error branch. Error message and session Info displayed below.
In the `no_error` branch there is no failure.  The only difference between the two branches is the presence of
`import(emayili)` in the `NAMESPACE` file in the error branch.

Also neither branch fails if the installed package version of emayili is <= 0.4.15

## Steps to reproduce

### Setup

[optional run on docker image] `docker run -it rocker/tidyverse bash`

```sh
git clone https://github.com/adam-gruer/errorReprex.git
```

```sh
Rscript -e 'install.packages("emayili")'
```

### Error
```sh 
R CMD INSTALL errorReprex
```

### No error

```sh 
cd errorReprex
```

```sh
git checkout no_error
```

```sh
cd ..
```

```sh
R CMD INSTALL errorReprex
```

### Install earlier version of emayili

```sh
Rscript -e 'devtools::install_version("emayili", "0.4.15")
```
 


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

## Session Info

```r
R version 4.1.1 (2021-08-10)
Platform: x86_64-pc-linux-gnu (64-bit)
Running under: Ubuntu 20.04.3 LTS

Matrix products: default
BLAS/LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.8.so

locale:
 [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C
 [3] LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8
 [5] LC_MONETARY=en_US.UTF-8    LC_MESSAGES=C
 [7] LC_PAPER=en_US.UTF-8       LC_NAME=C
 [9] LC_ADDRESS=C               LC_TELEPHONE=C
[11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base

loaded via a namespace (and not attached):
[1] compiler_4.1.1

```
