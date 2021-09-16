# errorReprex
reproducible example of an R package install error

the command ```R CMD INSTALL errorReprex``` fails in the error branch. Error message displayed below.
In the `no_error` branch there is no failure.  The only difference between the two branches is the presence of
`import(emayili)` in the `NAMESPACE` file in the error branch.

Also neither branch fails if the package version of emayili is <= 0.4.15

Steps to reproduce

[optional run on docker image]

`docker run -it rocker/tidyverse bash`

`git clone https://github.com/adam-gruer/errorReprex.git`

`Rscript -e 'install.packages("emayili")'`

`R CMD INSTALL errorReprex`

`cd errorReprex`

`git checkout no_error`

`cd ..`

`R CMD INSTALL errorReprex`



