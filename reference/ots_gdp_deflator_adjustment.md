# Expresses tidy data from the API in dollars of a reference year

Uses GDP deflator records from The World Bank to convert trade records
and express them in dollars of the same year. The records are internally
subsetted to World's values, because country specific levels would
largely re-scale observations for reporters that reflect unstable
macroeconomic policies.

## Usage

``` r
ots_gdp_deflator_adjustment(trade_data = NULL, reference_year = NULL)
```

## Arguments

- trade_data:

  A tibble obtained by using ots_create_tidy_data. Default set to
  `NULL`.

- reference_year:

  Year contained within the years specified in
  api.tradestatistics.io/year_range (e.g. `2010`). Default set to
  `NULL`.

## Examples

``` r
if (FALSE) { # \dontrun{
# The next example can take more than 5 seconds to compute,
# so this is shown without evaluation according to CRAN rules

# Convert dollars of 2010 to dollars of 2000
d <- ots_create_tidy_data(years = 2010, reporters = "chl", partners = "chn")
ots_gdp_deflator_adjustment(trade_data = d, reference_year = 2000)
} # }
```
