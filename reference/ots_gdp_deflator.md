# GDP Deflator

Year to year GDP deflator some of the countries in the OTS database. For
countries not available in the World Bank database, rows labelled as
"wld" are provided, which were computed as the weighted median for each
year using the GDP of listed countries for each year expressed as
constant dollars of the year 2010.

## Usage

``` r
ots_gdp_deflator
```

## Format

A data frame with 8,010 observations on the following 4 variables

- `year_from`:

  Integer values in the range 1980-2020

- `year_to`:

  Integer values in the range 1981-2021

- `country_iso`:

  ISO code of the country (e.g. "chl" means Chile)

- `gdp_deflator`:

  Numeric value expressed as one plus 1-year deflator

## Source

Open Trade Statistics
