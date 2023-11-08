
<!-- README.md is generated from README.Rmd. Please edit that file -->

# countr

## Count Values by Group

<!-- badges: start -->
<!-- badges: end -->

The goal of `countr` is to make generating summary tables more
efficient! It contains functions to help you save time in your
exploratory data analysis. Presently, the package contains a function to
count missing values in columns by group, outputting a summary tibble of
missing value counts.

## Installation

You can install the development version of `countr` from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("stat545ubc-2023/countr", ref = "0.1.0")
```

## Usage

One of the first steps in any exploratory data analysis is generating
summary tables that help you visualize the structure and quality of your
datasets. For example, a common first step is evaluating the proportion
of values missing for each of your variables in a dataset. This package
includes a function that can quickly create a summary table of missing
value counts.

## Examples

For example, let’s see how to count up all the missing values in the
`airquality` dataset by the `Month` variable:

``` r
# load the package
library(countr)

# run the function with the airquality dataset
count_all_missing_by_group(airquality, Month) 
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

Alternatively, you could pipe your dataset directly into the function
using the base R pipe, `|>`, or the magrittr pipe `%>%`:

``` r
# run the function using the pipe with the airquality dataset
airquality |> count_all_missing_by_group(Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

Finally, if you want your output tibble to remain grouped, specify the
`.groups` argument:

``` r
# specify the .groups argument
count_all_missing_by_group(airquality, Month, .groups = "keep")
#> # A tibble: 5 × 6
#> # Groups:   Month [5]
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```
