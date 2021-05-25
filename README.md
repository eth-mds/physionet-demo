## Drat Repo

A [`drat`](https://github.com/eddelbuettel/drat) repo for data packages [`mimic.demo`](https://github.com/eth-mds/mimic-demo) and [`eicu.demo`](https://github.com/eth-mds/eicu-demo), build using [`drat.builder`](https://github.com/richfitz/drat.builder). To add further packages, edit [packages.txt]. To rebuild, run

```r
remotes::install_github("richfitz/drat.builder")
drat.builder::build()
```
