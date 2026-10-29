# Downloads and processes the data from the API to return a human-readable tibble (unmemoised, internal)

A separation of
[`ots_create_tidy_data()`](https://docs.ropensci.org/tradestatistics/reference/ots_create_tidy_data.md)
for making caching optional.

## Usage

``` r
ots_create_tidy_data_unmemoised(
  years = 2018,
  reporters = "usa",
  partners = "all",
  commodities = "all",
  sections = "all",
  table = "yr",
  max_attempts = 5
)
```
