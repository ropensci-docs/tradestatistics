# Downloads and processes the data from the API to return a human-readable tibble

Accesses `api.tradestatistics.io` and performs different API calls to
transform and return tidy data.

## Usage

``` r
ots_create_tidy_data(
  years = 2020,
  reporters = "all",
  partners = "all",
  commodities = "all",
  sections = "all",
  table = "yr",
  max_attempts = 5,
  use_cache = FALSE,
  file = NULL
)
```

## Arguments

- years:

  Year contained within the years specified in
  api.tradestatistics.io/year_range (e.g. `c(2002,2004)`, `c(2002:2004)`
  or `2002`). Default set to `2019`.

- reporters:

  ISO code for reporter country (e.g. `"chl"`, `"Chile"` or
  `c("chl", "Peru")`). Default set to `"all"`.

- partners:

  ISO code for partner country (e.g. `"chl"`, `"Chile"` or
  `c("chl", "Peru")`). Default set to `"all"`.

- commodities:

  HS commodity codes (e.g. `"0101"`, `"01"` or search matches for
  `"apple"`) to filter commodities. Default set to `"all"`.

- sections:

  HS section codes (e.g. `"01"`). Default set to `"all"`.

- table:

  Character string to select the table to obtain the data. Default set
  to `yr` (Year - Reporter). Run `ots_tables` in case of doubt.

- max_attempts:

  How many times to try to download data in case the API or the internet
  connection fails when obtaining data. Default set to `5`.

- use_cache:

  Logical to save and load from cache. If `TRUE`, the results will be
  cached in memory if `file` is `NULL` or on disk if \`file\` is not
  `NULL`. Default set to `FALSE`.

- file:

  Optional character with the full file path to save the data. Default
  set to `NULL`.

## Value

A tibble that describes bilateral trade metrics (imports, exports, trade
balance and relevant metrics such as exports growth w/r to last year)
between a `reporter` and `partner` country.

## Examples

``` r
if (FALSE) { # \dontrun{
# The next examples can take more than 5 seconds to compute,
# so these are just shown without evaluation according to CRAN rules

# Run `ots_countries` to display the full table of countries
# Run `ots_commodities` to display the full table of commodities

# What does Chile export to China? (2002)
ots_create_tidy_data(years = 2002, reporters = "chl", partners = "chn")

# What can we say about Horses export in Chile and the World? (2002)
ots_create_tidy_data(years = 2002, commodities = "010110", table = "yc")
ots_create_tidy_data(years = 2002, reporters = "chl", commodities = "010110", table = "yrc")

# What can we say about the different types of apples exported by Chile? (2002)
ots_create_tidy_data(years = 2002, reporters = "chl", commodities = "apple", table = "yrc")
} # }
```
