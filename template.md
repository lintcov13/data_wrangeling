Data Import
================

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
    ## ✔ tibble  3.1.8     ✔ dplyr   1.0.9
    ## ✔ tidyr   1.2.0     ✔ stringr 1.4.0
    ## ✔ readr   2.1.1     ✔ forcats 0.5.1
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

## Data Import: CVs

Lets import data using the ‘readr’ package

``` r
litters_df = read_csv("data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
```

``` r
view(litters_df)
```

``` r
skimr::skim(litters_df)
```

|                                                  |            |
|:-------------------------------------------------|:-----------|
| Name                                             | litters_df |
| Number of rows                                   | 49         |
| Number of columns                                | 8          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |            |
| Column type frequency:                           |            |
| character                                        | 2          |
| numeric                                          | 6          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |            |
| Group variables                                  | None       |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| group         |         0 |             1 |   4 |   4 |     0 |        6 |          0 |
| litter_number |         0 |             1 |   3 |  15 |     0 |       49 |          0 |

**Variable type: numeric**

| skim_variable   | n_missing | complete_rate |  mean |   sd |   p0 |   p25 |   p50 |   p75 | p100 | hist  |
|:----------------|----------:|--------------:|------:|-----:|-----:|------:|------:|------:|-----:|:------|
| gd0_weight      |        15 |          0.69 | 24.38 | 3.28 | 17.0 | 22.30 | 24.10 | 26.67 | 33.4 | ▃▇▇▆▁ |
| gd18_weight     |        17 |          0.65 | 41.52 | 4.05 | 33.4 | 38.88 | 42.25 | 43.80 | 52.7 | ▃▃▇▂▁ |
| gd_of_birth     |         0 |          1.00 | 19.65 | 0.48 | 19.0 | 19.00 | 20.00 | 20.00 | 20.0 | ▅▁▁▁▇ |
| pups_born_alive |         0 |          1.00 |  7.35 | 1.76 |  3.0 |  6.00 |  8.00 |  8.00 | 11.0 | ▁▃▂▇▁ |
| pups_dead_birth |         0 |          1.00 |  0.33 | 0.75 |  0.0 |  0.00 |  0.00 |  0.00 |  4.0 | ▇▂▁▁▁ |
| pups_survive    |         0 |          1.00 |  6.41 | 2.05 |  1.0 |  5.00 |  7.00 |  8.00 |  9.0 | ▁▃▂▇▇ |

‘read_csv’ options… -can change the NA -how many rows you want to skip

``` r
read_csv("data/FAS_litters.csv", na = c("", "NA", 999, 88), skip = 2)
```

##Other file formats

we need to read in an excel spreadsheet…

``` r
read_excel("data/mlb11.xlsx")
```

    ## # A tibble: 30 × 12
    ##    team         runs at_bats  hits homer…¹ bat_avg strik…² stole…³  wins new_o…⁴
    ##    <chr>       <dbl>   <dbl> <dbl>   <dbl>   <dbl>   <dbl>   <dbl> <dbl>   <dbl>
    ##  1 Texas Rang…   855    5659  1599     210   0.283     930     143    96   0.34 
    ##  2 Boston Red…   875    5710  1600     203   0.28     1108     102    90   0.349
    ##  3 Detroit Ti…   787    5563  1540     169   0.277    1143      49    95   0.34 
    ##  4 Kansas Cit…   730    5672  1560     129   0.275    1006     153    71   0.329
    ##  5 St. Louis …   762    5532  1513     162   0.273     978      57    90   0.341
    ##  6 New York M…   718    5600  1477     108   0.264    1085     130    77   0.335
    ##  7 New York Y…   867    5518  1452     222   0.263    1138     147    97   0.343
    ##  8 Milwaukee …   721    5447  1422     185   0.261    1083      94    96   0.325
    ##  9 Colorado R…   735    5544  1429     163   0.258    1201     118    73   0.329
    ## 10 Houston As…   615    5598  1442      95   0.258    1164     118    56   0.311
    ## # … with 20 more rows, 2 more variables: new_slug <dbl>, new_obs <dbl>, and
    ## #   abbreviated variable names ¹​homeruns, ²​strikeouts, ³​stolen_bases,
    ## #   ⁴​new_onbase
    ## # ℹ Use `print(n = ...)` to see more rows, and `colnames()` to see all variable names

##Still more file formats

read in a SAS dataset

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## Data export

``` r
write_csv(pulse_df, file = "data/pulse_df.csv") 
```
