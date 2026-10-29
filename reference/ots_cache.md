# Caching wrapper to reduce API calls (internal)

Eases saving the data downloaded from `api.tradestatistics.io` and
prevents
[`ots_read_from_api()`](https://docs.ropensci.org/tradestatistics/reference/ots_read_from_api.md)
from downloading the same twice.

## Usage

``` r
ots_cache(use_cache, file, ...)
```

## Arguments

- use_cache:

  Logical to save and load from cache. If `TRUE`, the results will be
  cached in memory if `file` is `NULL` or on disk if \`file\` is not
  `NULL`.

- file:

  Character with the full file path to save the data.

- ...:

  Additional parameters inherited from
  [`ots_create_tidy_data()`](https://docs.ropensci.org/tradestatistics/reference/ots_create_tidy_data.md).
