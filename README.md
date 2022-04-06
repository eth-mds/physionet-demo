## Drat Repo

[![Build status](https://github.com/eth-mds/physionet-demo/workflows/build/badge.svg)](https://github.com/eth-mds/physionet-demo/actions?query=workflow%3Abuild)

A [`drat`](https://github.com/eddelbuettel/drat) repo for data packages [`mimic.demo`](https://github.com/eth-mds/mimic-demo) and [`eicu.demo`](https://github.com/eth-mds/eicu-demo), build using [`drat.builder`](https://github.com/richfitz/drat.builder). To add further packages, edit [packages.txt]. To rebuild, run

```r
remotes::install_github("nbenn/drat.builder")
drat.builder::build()
```
