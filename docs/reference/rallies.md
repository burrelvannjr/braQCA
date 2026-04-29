# McVeigh et al. (2014) Tea Party Data

This data set is an abbreviated version of the data set used by McVeigh
et al. (2014). These data cover all 67 counties in Florida, and come
from the American Community Survey (2005-2009).

## Usage

``` r
rallies
```

## Format

A data frame with 67 observations and 13 variables.

|  |  |
|----|----|
|  | tprallies |
| number of Tea Party rallies in county, 2009-2010 | reppct2008 |
| percent of county vote for the Republican Presidential candidate (John McCain) in 2008 | dempct2008 |
| percent of county vote for the Democratic Presidential candidate (Barack Obama) in 2008 | pctBA25 |
| percent of county, aged 25 or older, with a bachelor's degree | pctunemp |
| percent of county that is unemployed | pctevang |
| percent of county that belongs to an Evangelical denomination | pctblack |
| percent of county that identifies as Black | P |
| binary. `0` if county had no Tea Party rallies, `1` if county had *at least* on Tea Party rally | R |
| binary. `0` if the majority of votes in the county were for the Democratic Presidential candidate (Barack Obama) in 2008, `1` if the majority of votes in the county were for the Republican Presidential candidate (John McCain) in 2008 | C |
| binary. `0` if percent of county with a bachelor's degree was below-average for Florida, `1` if percent of county with a bachelor's degree was at or above-average for Florida | U |
| binary. `0` if percent unemployed in county was below-average for Florida, `1` if percent unemployed in county was at or above-average for Florida | E |
| binary. `0` if percent Evangelical in county was below-average for Florida, `1` if percent Evangelical in county was at or above-average for Florida | B |
| binary. `0` if percent Black in county was below-average for Florida, `1` if percent Black in county was at or above-average for Florida |  |
