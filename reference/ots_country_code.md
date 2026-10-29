# String matching of official country names and ISO-3 codes according to the United Nations nomenclature

Takes a text string and searches within the package data for a country
code in the context of valid API country codes.

## Usage

``` r
ots_country_code(countryname = NULL)
```

## Arguments

- countryname:

  A text string such as "Chile", "CHILE" or "CHL".

## Value

A single character if there is a exact match (e.g.
`ots_country_code("Chile")`) or a tibble in case of multiple matches
(e.g. `ots_country_code("Germany")`)

## Examples

``` r
ots_country_code("Chile ")
#>    country_iso country_name_english country_fullname_english
#>         <char>               <char>                   <char>
#> 1:         chl                Chile                    Chile
#>    continent_name_english continent_id
#>                    <char>        <int>
#> 1:               Americas            2
ots_country_code("america")
#>    country_iso country_name_english
#>         <char>               <char>
#> 1:         usa                  USA
#>                                                       country_fullname_english
#>                                                                         <char>
#> 1: USA, Puerto Rico and US Virgin Islands (excludes Virgin Islands until 1981)
#>    continent_name_english continent_id
#>                    <char>        <int>
#> 1:               Americas            2
ots_country_code("UNITED  STATES")
#> Empty data.table (0 rows and 5 cols): country_iso,country_name_english,country_fullname_english,continent_name_english,continent_id
ots_country_code(" united_")
#>    country_iso                 country_name_english
#>         <char>                               <char>
#> 1:         are                 United Arab Emirates
#> 2:         gbr                       United Kingdom
#> 3:         tza              United Rep. of Tanzania
#> 4:         umi United States Minor Outlying Islands
#> 5:         vir                    US Virgin Islands
#>                country_fullname_english continent_name_english continent_id
#>                                  <char>                 <char>        <int>
#> 1:                 United Arab Emirates                   Asia            4
#> 2:                       United Kingdom                 Europe            5
#> 3:              United Rep. of Tanzania                 Africa            1
#> 4: United States Minor Outlying Islands               Americas            2
#> 5:         United States Virgin Islands               Americas            2
```
