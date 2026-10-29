# Downloads and processes the data from the API to return a human-readable tibble (memoised, internal)

A composition of
[`ots_create_tidy_data_unmemoised()`](https://docs.ropensci.org/tradestatistics/reference/ots_create_tidy_data_unmemoised.md)
and `memoise()` for caching the output

## Usage

``` r
ots_create_tidy_data_memoised(
  years = 2018,
  reporters = "usa",
  partners = "all",
  commodities = "all",
  sections = "all",
  table = "yr",
  max_attempts = 5
)
```
