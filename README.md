
<!-- README.md is generated from README.Rmd. Please edit that file -->

# wisselstroom <img src="man/figures/logo.png" align="right" height="139" alt="" />

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![R-CMD-check](https://github.com/ed2c/wisselstroom/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/ed2c/wisselstroom/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

Each Higher Educational Institute (HEI) in the Netherlands can request
its institute-specific files named “Bekostigingsbestanden”. The
functions in this package extract information from these files related
to switching and continuing studies. It facilitates the HEIs gain
insight in the prevalence of switching and/or continuing studies. Flows
can be visualised by a Sankey diagram.

## Installation

You can install the development version of wisselstroom from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("ed2c/wisselstroom")
```

If you want to have the vignettes as well:

``` r
devtools::install_github("ed2c/wisselstroom", dependencies = TRUE, build_vignettes = TRUE)
```

## Example

Read in your VLPBEK bekostigingsbestand file with `read_bek_data()`:

``` r
path_to_file <- here::here("extdata", "VLPBEK_2025_20240115_99XX.csv")
my_vlpbek_data <- read_bek_data(path_to_file)
```

This results in one large data set. Hidden in that data set are
different sub data sets, which contain information about enrolment and
degrees.

To ease the access to this information, make a `flow_basics` object with
the function `make_flow_basics()`:

``` r
my_flow_basics <- make_flow_basics(my_vlpbek_data)
```

Gain insights by using the `make_flow_insights()` function. The
resulting object contains summary information related to switching HEIs
and/or programs, which can be plotted using for instance
`plot_brinflows()`:

``` r
my_flow_insights <- make_flow_insights(my_flow_basics)
plot_brinflows(my_flow_insights, display_labels = TRUE)
```

## Vignettes

Read the introduction vignette with more background information:

``` r
vignette("wisselstroom", package = "wisselstroom")
```

Browse the vignettes:

``` r
browseVignettes("wisselstroom")
```

## Citation

``` r
citation("wisselstroom")
#> To cite package 'wisselstroom' in publications use:
#> 
#>   Jansen M (2024). _wisselstroom, an R package to obtain insight in
#>   patterns of study programme switch_.
#> 
#> A BibTeX entry for LaTeX users is
#> 
#>   @Manual{,
#>     title = {{wisselstroom}, an R package to obtain insight in patterns of study programme switch},
#>     author = {Martine Jansen},
#>     publisher = {Center for Educational Data Analytics (CEDA), NPuls},
#>     year = {2024},
#>   }
```

## Acknowledgements

- Thank you Npuls and Fontys University of Applied Sciences for
  providing the opportunity to develop this package
- Thank you co-workers from Fontys University of Applied Sciences for
  your interesting questions regarding switch
- Thank you Corneel, Bram, Tomer, Amir, Tony and Damiette for your
  valuable input
- The code for the Sankey diagram is adapted from code found end of may
  2024 at <https://github.com/ssp3nc3r/ggSankeyGrad>
