# Basic usage

## Introduction

This vignette explains the functions within this package. The idea is to
show how this package simplifies obtaining data from
(api.tradestatistics.io)\[<https://api.tradestatistics.io>\].

To improve the presentation of the tables I shall use `tibble` besides
`tradestatistics`.

``` r

library(tradestatistics)
library(tibble)
```

## Package data

### Available tables

Provided that this package obtains data from an API, it is useful to
know which tables can be accessed:

``` r

as_tibble(ots_tables)
#> # A tibble: 12 × 3
#>    table             description                                          source
#>    <chr>             <chr>                                                <chr> 
#>  1 commodities       Commodities metadata (HS codes, 6 digits long)       Based…
#>  2 commodities_short Commodities metadata (HS codes, 4 digits long)       Based…
#>  3 countries         Countries metadata                                   Based…
#>  4 countries_colors  Countries colors                                     Open …
#>  5 sections          Sections metadata (HS codes)                         Based…
#>  6 sections_colors   Sections colors (HS codes)                           Open …
#>  7 year_range        Minimum and maximum years with available data        Based…
#>  8 yc                Commodity trade at aggregated level (Year and Commo… Based…
#>  9 yr                Reporter trade at aggregated level (Year and Report… Based…
#> 10 yrc               Reporter trade at commodity level (Year, Reporter a… Based…
#> 11 yrp               Reporter-Partner trade at aggregated level (Year, R… Based…
#> 12 yrpc              Reporter-Partner trade at commodity level (Year, Re… Based…
```

You might notice the tables have a pattern. The letters indicate the
presence of columns that account for the level of detail in the data:

- `y`: *y*ear column.
- `r`: *r*eporter column
- `p`: *p*artner column
- `c`: *c*ommodity column

The most aggregated table is `yr` which basically says how many dollars
each country exports and imports for a given year.

The less aggregated table is `yrpc` which says how many dollars of each
of the 1,242 commodities from the Harmonized System each country exports
to other countries and imports from other countries.

For the complete detail you can check
[tradestatistics.io](https://tradestatistics.io).

### Country codes

The Package Functions section explains that you don’t need to memorize
all ISO codes. The functions within this package are designed to match
strings (i.e. “United States” or “America”) to valid ISO codes
(i.e. “USA”).

Just as a reference, the table with all valid ISO codes can be accessed
by running this:

``` r

as_tibble(ots_countries)
#> # A tibble: 275 × 5
#>    country_iso country_name_english                       country_fullname_eng…¹
#>    <chr>       <chr>                                      <chr>                 
#>  1 abw         Aruba                                      Aruba                 
#>  2 afg         Afghanistan                                Afghanistan           
#>  3 ago         Angola                                     Angola                
#>  4 aia         Anguilla                                   Anguilla              
#>  5 alb         Albania                                    Albania               
#>  6 all         Alias for all valid ISO codes in the World NA                    
#>  7 and         Andorra                                    Andorra               
#>  8 ant         Neth. Antilles                             Neth. Antilles        
#>  9 are         United Arab Emirates                       United Arab Emirates  
#> 10 arg         Argentina                                  Argentina             
#> # ℹ 265 more rows
#> # ℹ abbreviated name: ¹​country_fullname_english
#> # ℹ 2 more variables: continent_name_english <chr>, continent_id <int>
```

### Commodity codes

The Package Functions section explains that you don’t need to memorize
all HS codes. The functions within this package are designed to match
strings (i.e. “apple”) to valid HS codes (i.e. “0808”).

``` r

as_tibble(ots_commodities)
#> # A tibble: 5,302 × 4
#>    commodity_code commodity_code_short commodity_fullname_english   section_code
#>    <chr>          <chr>                <chr>                        <chr>       
#>  1 010121         0101                 Horses; live, pure-bred bre… 01          
#>  2 010129         0101                 Horses; live, other than pu… 01          
#>  3 010130         0101                 Asses; live                  01          
#>  4 010190         0101                 Mules and hinnies; live      01          
#>  5 010221         0102                 Cattle; live, pure-bred bre… 01          
#>  6 010229         0102                 Cattle; live, other than pu… 01          
#>  7 010231         0102                 Buffalo; live, pure-bred br… 01          
#>  8 010239         0102                 Buffalo; live, other than p… 01          
#>  9 010290         0102                 Bovine animals; live, other… 01          
#> 10 010310         0103                 Swine; live, pure-bred bree… 01          
#> # ℹ 5,292 more rows
```

### Inflation data

This table is provided to be used with
[`ots_gdp_deflator_adjustment()`](https://docs.ropensci.org/tradestatistics/reference/ots_gdp_deflator_adjustment.md).

``` r

as_tibble(ots_gdp_deflator)
#> # A tibble: 8,010 × 4
#>    year_from year_to country_iso gdp_deflator
#>        <int>   <int> <chr>              <dbl>
#>  1      1986    1987 abw                 1.04
#>  2      1987    1988 abw                 1.03
#>  3      1988    1989 abw                 1.04
#>  4      1989    1990 abw                 1.06
#>  5      1990    1991 abw                 1.06
#>  6      1991    1992 abw                 1.04
#>  7      1992    1993 abw                 1.05
#>  8      1993    1994 abw                 1.06
#>  9      1994    1995 abw                 1.03
#> 10      1995    1996 abw                 1.03
#> # ℹ 8,000 more rows
```

## Package functions

### Country code

The end user can use this function to find an ISO code by providing a
country name. This works by implementing partial search.

Basic examples:

``` r

# Single match with no replacement
as_tibble(ots_country_code("Chile"))
#> # A tibble: 1 × 5
#>   country_iso country_name_english country_fullname_eng…¹ continent_name_english
#>   <chr>       <chr>                <chr>                  <chr>                 
#> 1 chl         Chile                Chile                  Americas              
#> # ℹ abbreviated name: ¹​country_fullname_english
#> # ℹ 1 more variable: continent_id <int>

# Single match with replacement
as_tibble(ots_country_code("America"))
#> # A tibble: 1 × 5
#>   country_iso country_name_english country_fullname_eng…¹ continent_name_english
#>   <chr>       <chr>                <chr>                  <chr>                 
#> 1 usa         USA                  USA, Puerto Rico and … Americas              
#> # ℹ abbreviated name: ¹​country_fullname_english
#> # ℹ 1 more variable: continent_id <int>

# Double match with no replacement
as_tibble(ots_country_code("Germany"))
#> # A tibble: 1 × 5
#>   country_iso country_name_english country_fullname_eng…¹ continent_name_english
#>   <chr>       <chr>                <chr>                  <chr>                 
#> 1 deu         Germany              Germany (former Feder… Europe                
#> # ℹ abbreviated name: ¹​country_fullname_english
#> # ℹ 1 more variable: continent_id <int>
```

The function
[`ots_country_code()`](https://docs.ropensci.org/tradestatistics/reference/ots_country_code.md)
is used by
[`ots_create_tidy_data()`](https://docs.ropensci.org/tradestatistics/reference/ots_create_tidy_data.md)
in a way that you can pass parameters like
`ots_create_tidy_data(... reporters = "Chile" ...)` and it will
automatically replace your input for a valid ISO in case there is a
match. This will be covered in detail in the Trade Data section.

### Commodity code

The end user can find a code or a set of codes by looking for keywords
for commodities or groups. The function
[`ots_commodity_code()`](https://docs.ropensci.org/tradestatistics/reference/ots_commodity_code.md)
allows to search from the official commodities and groups in the
Harmonized system:

``` r

as_tibble(ots_commodity_code(commodity = " Horse ", section = " ANIMAL "))
#> # A tibble: 8 × 5
#>   section_code commodity_code commodity_code_short commodity_fullname_english   
#>   <chr>        <chr>          <chr>                <chr>                        
#> 1 01           010121         0101                 Horses; live, pure-bred bree…
#> 2 01           010129         0101                 Horses; live, other than pur…
#> 3 01           020500         0205                 Meat; of horses, asses, mule…
#> 4 01           020680         0206                 Offal, edible; of sheep, goa…
#> 5 01           020690         0206                 Offal, edible; of sheep, goa…
#> 6 01           030245         0302                 Fish; fresh or chilled, jack…
#> 7 01           030355         0303                 Fish; frozen, jack and horse…
#> 8 01           050290         0502                 Animal products; badger hair…
#> # ℹ 1 more variable: section_fullname_english <chr>
```

### Trade data

This function downloads data for a single year and needs (at least) some
filter parameters according to the query type.

Here we cover aggregated tables to describe the usage.

#### Bilateral trade at commodity level (Year - Reporter - Partner - Commodity Code)

If we want Chile-Argentina bilateral trade at community level in 2019:

``` r

yrpc <- ots_create_tidy_data(
  years = 2019,
  reporters = "chl",
  partners = "arg",
  table = "yrpc"
)

as_tibble(yrpc)
```

We can pass two years or more, several reporters/partners, and filter by
commodities with exact codes or code matching based on keywords:

``` r

# Note that here I'm passing Peru and not per which is the ISO code for Peru
# The same applies to Brazil
yrpc2 <- ots_create_tidy_data(
  years = 2018:2019,
  reporters = c("chl", "Peru", "bol"),
  partners = c("arg", "Brazil"),
  commodities = c("01", "food"),
  table = "yrpc"
)
```

The `yrpc` table returns some fields that deserve an explanation which
can be seen at [tradestatistics.io](https://tradestatistics.io). This
example is interesting because “01” return a set of commodities (all
commodities starting with 01, which is the commodity group “Animals;
live”), but “food” return all commodities with a matching description
(“1601”, “1806”, “1904”, etc.). In addition, not all the requested
commodities are exported from each reporter to each partner, therefore a
warning is returned.

#### Bilateral trade at aggregated level (Year - Reporter - Partner)

If we want Chile-Argentina bilateral trade at aggregated level in 2018
and 2019:

``` r

yrp <- ots_create_tidy_data(
  years = 2018:2019,
  reporters = c("chl", "per"),
  partners = "arg",
  table = "yrp"
)
```

This table accepts different years, reporters and partners just like
`yrpc`.

#### Reporter trade at commodity level (Year - Reporter - Commodity Code)

If we want Chilean trade at commodity level in 2019 with respect to
commodity “010121” which means “Horses; live, pure-bred breeding
animals”:

``` r

yrc <- ots_create_tidy_data(
  years = 2019,
  reporters = "chl",
  commodities = "010121",
  table = "yrc"
)
```

This table accepts different years, reporters and commodity codes just
like `yrpc`.

All the variables from this table are documented at
[tradestatistics.io](https://tradestatistics.io).

#### Reporter trade at aggregated level (Year - Reporter)

If we want the aggregated trade of Chile, Argentina and Peru in 2018 and
2019:

``` r

yr <- ots_create_tidy_data(
  years = 2018:2019,
  reporters = c("chl", "arg", "per"),
  table = "yr"
)
```

This table accepts different years and reporters just like `yrpc`.

All the variables from this table are documented at
[tradestatistics.io](https://tradestatistics.io).

#### Commodity trade at aggregated level (Year - Commodity Code)

If we want all commodities traded in 2019:

``` r

yc <- ots_create_tidy_data(
  years = 2019,
  table = "yc"
)
```

If we want the traded values of the commodity “010121” which means
“Horses; live, pure-bred breeding animals” in 2019:

``` r

yc2 <- ots_create_tidy_data(
  years = 2019,
  commodities = "010121",
  table = "yc"
)
```

This table accepts different years just like `yrpc`.

### Inflation adjustment

Taking the `yr` table from above, we can use
[`ots_gdp_deflator_adjustment()`](https://docs.ropensci.org/tradestatistics/reference/ots_gdp_deflator_adjustment.md)
to convert dollars from 2018 and 2019 to dollars of 2000:

``` r

inflation <- ots_gdp_deflator_adjustment(yr, reference_year = 2000)
as_tibble(inflation)
```
