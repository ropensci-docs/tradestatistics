# Reads data from the API (internal function)

Accesses `api.tradestatistics.io` and performs different API calls to
return `data.frames` by reading `JSON` data. The parameters here are
passed from `ots_create_tidy_data`.

## Usage

``` r
ots_read_from_api(
  year = NULL,
  reporter_iso = NULL,
  partner_iso = NULL,
  commodity_code = "all",
  section_code = "all",
  table = "yr",
  max_attempts = 5
)
```
