
<!-- README.md is generated from README.Rmd. Please edit that file -->
dkbi
====

[![lifecycle](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)

A general purpose package for Dankegongyu business intelligence unit.

Installation
------------

You can install the development version of dkbi from internal RStudio package manager.

``` r
install.packages("dkbi", repos = "<internal-cran>")
```

Required Variables
------------------

By default, `dkbi` will look for an `consul` object in your R global environment. It is recommended to set the following system variables in your `.Renviron` file.

``` r
consul.host = "some host"
consul.port = "some port"
consul.swagger = "some swagger"
consul.secret = "some secret"
```

Common Workflow
---------------

`dkbi` helps to fetch values from KV store and make connection to databases.

``` r
library(dkbi)

# initiate config.R to specific path
init_config(path = "R/")

# source configs
source("R/config.R")

# make connection to database
est_mysql_conn("Forecast")
```

``` bash
<MySQLConnection:0,0>
```

``` r
# fetch parameters from KV store
get_batch_kv("some_api_params", "host", "port", "swagger")
```

``` bash
$host
[1] "some_api_host"

$port
[1] "some_api_port"

$swagger
[1] "some_api_swagger"
```

Available Commands
------------------

``` r
library(dkbi)
ls('package:dkbi')
#> [1] "est_mongo_conn" "est_mysql_conn" "get_batch_kv"   "get_kv"        
#> [5] "init_config"    "init_plumber"   "init_script"
```
