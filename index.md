dplyr filter homework
================
Piret Saar-Reismaa
2019-03-12

### Exercises

Loading required
    libraries:

``` r
library(tidyverse)
```

    ## ── Attaching packages ────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.1.0       ✔ purrr   0.3.0  
    ## ✔ tibble  2.0.1       ✔ dplyr   0.8.0.1
    ## ✔ tidyr   0.8.2       ✔ stringr 1.4.0  
    ## ✔ readr   1.3.1       ✔ forcats 0.4.0

    ## ── Conflicts ───────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(here)
```

    ## here() starts at /cloud/project

Importing dataset:

``` r
viruses <- read_csv(here("data", "viruses.csv"))
```

    ## Parsed with column specification:
    ## cols(
    ##   organism_name = col_character(),
    ##   tax_id = col_double(),
    ##   bioproject_accession = col_character(),
    ##   bioproject_id = col_double(),
    ##   group = col_character(),
    ##   subgroup = col_character(),
    ##   size_kb = col_double(),
    ##   gc = col_double(),
    ##   host = col_character(),
    ##   segments = col_character(),
    ##   genes = col_character(),
    ##   proteins = col_character(),
    ##   release_date = col_date(format = ""),
    ##   modify_date = col_date(format = ""),
    ##   status = col_character()
    ## )

Print out dataset:

``` r
viruses
```

    ## # A tibble: 28,740 x 15
    ##    organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##    <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ##  1 Escherichia … 1.44e6 PRJNA485481             485481 dsDN… Podovir…
    ##  2 Enterovirus J 1.33e6 PRJNA485481             485481 ssRN… Picorna…
    ##  3 Bacilladnavi… 2.27e6 PRJNA393166             393166 ssDN… Bacilla…
    ##  4 Invertebrate… 1.30e6 PRJNA485481             485481 dsDN… Iridovi…
    ##  5 Invertebrate… 3.46e5 PRJNA485481             485481 dsDN… Iridovi…
    ##  6 Bacillus pha… 1.41e6 PRJNA485481             485481 dsDN… Siphovi…
    ##  7 Salmonella p… 1.41e6 PRJNA485481             485481 dsDN… Ackerma…
    ##  8 Brevibacillu… 1.30e6 PRJNA485481             485481 dsDN… Myoviri…
    ##  9 Mycobacteriu… 1.08e6 PRJNA485481             485481 dsDN… Siphovi…
    ## 10 Mycobacteriu… 1.07e6 PRJNA485481             485481 dsDN… Siphovi…
    ## # … with 28,730 more rows, and 9 more variables: size_kb <dbl>, gc <dbl>,
    ## #   host <chr>, segments <chr>, genes <chr>, proteins <chr>,
    ## #   release_date <date>, modify_date <date>, status <chr>

1.  Find all viruses that:

<!-- end list -->

  - have genome of over 10000kb

<!-- end list -->

``` r
filter(viruses, size_kb > 10000)
```

    ## # A tibble: 8 x 15
    ##   organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##   <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ## 1 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 2 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 3 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 4 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 5 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 6 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 7 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## 8 uncultured m… 186617 PRJDB4437               371593 Other Other   
    ## # … with 9 more variables: size_kb <dbl>, gc <dbl>, host <chr>,
    ## #   segments <chr>, genes <chr>, proteins <chr>, release_date <date>,
    ## #   modify_date <date>, status <chr>

  - belong to *Papillomaviridae*

<!-- end list -->

``` r
filter(viruses, subgroup == "Papillomaviridae")
```

    ## # A tibble: 395 x 15
    ##    organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##    <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ##  1 Canis famili… 1.23e6 PRJNA485481             485481 dsDN… Papillo…
    ##  2 Enhydra lutr… 1.47e6 PRJNA485481             485481 dsDN… Papillo…
    ##  3 Pygoscelis a… 1.48e6 PRJNA485481             485481 dsDN… Papillo…
    ##  4 Human papill… 1.48e6 PRJNA485481             485481 dsDN… Papillo…
    ##  5 Rupicapra ru… 1.16e6 PRJNA485481             485481 dsDN… Papillo…
    ##  6 Saimiri sciu… 9.90e5 PRJNA485481             485481 dsDN… Papillo…
    ##  7 Fulmarus gla… 1.46e6 PRJNA485481             485481 dsDN… Papillo…
    ##  8 Apodemus syl… 1.04e6 PRJNA485481             485481 dsDN… Papillo…
    ##  9 Human papill… 1.32e6 PRJNA485481             485481 dsDN… Papillo…
    ## 10 Human papill… 1.47e6 PRJNA485481             485481 dsDN… Papillo…
    ## # … with 385 more rows, and 9 more variables: size_kb <dbl>, gc <dbl>,
    ## #   host <chr>, segments <chr>, genes <chr>, proteins <chr>,
    ## #   release_date <date>, modify_date <date>, status <chr>

  - are from plants and environment

<!-- end list -->

``` r
filter(viruses, host == "plants"| host== "environment")
```

    ## # A tibble: 2,816 x 15
    ##    organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##    <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ##  1 Pouzolzia go… 1.23e6 PRJNA485481             485481 ssDN… Geminiv…
    ##  2 Nepavirus     1.22e6 PRJNA485481             485481 ssDN… unclass…
    ##  3 Baminivirus   1.23e6 PRJNA485481             485481 ssDN… Geminiv…
    ##  4 Niminivirus   1.23e6 PRJNA485481             485481 ssDN… Geminiv…
    ##  5 Axonopus com… 1.48e6 PRJNA485481             485481 ssDN… Geminiv…
    ##  6 Andrographis… 1.48e6 PRJNA485481             485481 Sate… Tolecus…
    ##  7 Faba bean ne… 1.44e6 PRJNA485481             485481 Sate… Alphasa…
    ##  8 Black medic … 1.44e6 PRJNA485481             485481 Sate… Alphasa…
    ##  9 Cyanoramphus… 1.28e6 PRJNA485481             485481 ssDN… unclass…
    ## 10 Cyanoramphus… 1.28e6 PRJNA485481             485481 ssDN… unclass…
    ## # … with 2,806 more rows, and 9 more variables: size_kb <dbl>, gc <dbl>,
    ## #   host <chr>, segments <chr>, genes <chr>, proteins <chr>,
    ## #   release_date <date>, modify_date <date>, status <chr>

  - were released between 01. January 1980 - 01. January 1990, including
    these
days:

<!-- end list -->

``` r
filter(viruses, release_date >= "1980-01-01", release_date <= "1990-01-01")
```

    ## # A tibble: 113 x 15
    ##    organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##    <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ##  1 Enterobacter… 1.09e4 <NA>                         0 ssDN… Inoviri…
    ##  2 Enterobacter… 1.09e4 PRJNA485481             485481 ssDN… Inoviri…
    ##  3 Enterobacter… 1.08e4 PRJNA485481             485481 ssDN… Microvi…
    ##  4 Enterobacter… 1.20e4 PRJNA485481             485481 ssRN… Levivir…
    ##  5 Human polyom… 1.89e6 PRJNA485481             485481 dsDN… Polyoma…
    ##  6 Mesocricetus… 1.89e6 PRJNA485481             485481 dsDN… Polyoma…
    ##  7 Escherichia … 1.08e4 PRJNA485481             485481 ssDN… Microvi…
    ##  8 Escherichia … 1.98e6 PRJNA485481             485481 ssDN… Inoviri…
    ##  9 Ateline gamm… 1.04e4 PRJNA485481             485481 dsDN… Herpesv…
    ## 10 Avian carcin… 1.19e4 PRJNA485481             485481 Other Retrovi…
    ## # … with 103 more rows, and 9 more variables: size_kb <dbl>, gc <dbl>,
    ## #   host <chr>, segments <chr>, genes <chr>, proteins <chr>,
    ## #   release_date <date>, modify_date <date>, status <chr>

2.  there is also between() function in dplyr.

What does it do? Run ?between How can you use it to find viruses with
genomes between 1 to 2 kb?

``` r
?between
```

It is a shortcut to writing x bigger than and x smaller than, it
automatically knows that they are the boundary values. between(x, left,
right), where x is the vector from where the boundary values search is
implemented on.

``` r
filter(viruses, between(size_kb,1,2))
```

    ## # A tibble: 4,675 x 15
    ##    organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##    <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ##  1 Dragonfly cy… 1.23e6 PRJNA485481             485481 ssDN… unclass…
    ##  2 Dragonfly or… 1.23e6 PRJNA485481             485481 ssDN… unclass…
    ##  3 Dragonfly as… 1.23e6 PRJNA485481             485481 ssDN… Circovi…
    ##  4 Dragonfly as… 1.23e6 PRJNA485481             485481 ssDN… Circovi…
    ##  5 Dragonfly as… 1.23e6 <NA>                         0 ssDN… Circovi…
    ##  6 Dragonfly as… 1.23e6 PRJNA485481             485481 ssDN… Circovi…
    ##  7 Andrographis… 1.48e6 PRJNA485481             485481 Sate… Tolecus…
    ##  8 Mink circovi… 1.48e6 PRJNA485481             485481 ssDN… Circovi…
    ##  9 Faba bean ne… 1.44e6 PRJNA485481             485481 Sate… Alphasa…
    ## 10 Black medic … 1.44e6 PRJNA485481             485481 Sate… Alphasa…
    ## # … with 4,665 more rows, and 9 more variables: size_kb <dbl>, gc <dbl>,
    ## #   host <chr>, segments <chr>, genes <chr>, proteins <chr>,
    ## #   release_date <date>, modify_date <date>, status <chr>

3.  Find Enteroviruses:

Hint: use str\_detect()

``` r
filter(viruses, str_detect(organism_name, "Enterovirus"))
```

    ## # A tibble: 9 x 15
    ##   organism_name tax_id bioproject_acce… bioproject_id group subgroup
    ##   <chr>          <dbl> <chr>                    <dbl> <chr> <chr>   
    ## 1 Enterovirus J 1.33e6 PRJNA485481             485481 ssRN… Picorna…
    ## 2 Enterovirus … 4.77e4 PRJNA485481             485481 ssRN… Picorna…
    ## 3 Enterovirus … 1.83e6 PRJNA485481             485481 ssRN… Picorna…
    ## 4 Enterovirus … 1.93e6 PRJNA485481             485481 ssRN… Picorna…
    ## 5 Enterovirus … 1.85e6 PRJNA485481             485481 ssRN… Picorna…
    ## 6 Enterovirus E 1.21e4 PRJNA485481             485481 ssRN… Picorna…
    ## 7 Enterovirus F 1.33e6 PRJNA485481             485481 ssRN… Picorna…
    ## 8 Enterovirus … 4.28e4 PRJNA485481             485481 ssRN… Picorna…
    ## 9 Enterovirus J 1.33e6 PRJNA485481             485481 ssRN… Picorna…
    ## # … with 9 more variables: size_kb <dbl>, gc <dbl>, host <chr>,
    ## #   segments <chr>, genes <chr>, proteins <chr>, release_date <date>,
    ## #   modify_date <date>, status <chr>
