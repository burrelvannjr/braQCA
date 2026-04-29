# Configuration Table

Internal function; calculates via logistic regression the output of the
Bootstrapped Robustness Recommendation

## Usage

``` r
conf.table(data, ncut = ncut)
```

## Arguments

- data:

  name of the model object; the table of solutions for an application of
  QCA. Default set to `data`.

- ncut:

  configurational n levels for inclusion. Default set to `ncut=4`

## Value

The output of the Bootstrapped Recommendation \#' @export
