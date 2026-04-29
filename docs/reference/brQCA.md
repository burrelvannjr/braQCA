# Bootstrapped Recommendation

Provides recommendations for consistency score and configurational n
thresholds to attain a desired level of confidence in a QCA algorithm
application.

## Usage

``` r
brQCA(
  qca.data,
  outcome = "OUT",
  type = "crisp",
  inclcut = "",
  ncut = 2,
  neg.out = FALSE,
  sim = 10,
  verbose = TRUE
)
```

## Arguments

- qca.data:

  the QCA data frame.

- outcome:

  the outcome variable in the QCA data frame of causal conditions;
  `"OUT"` is the outcome variable for an application of QCA.

- type:

  of QCA application, `"crisp"` or `"fuzzy"` sets. Default set to
  `type = "crisp"`.

- inclcut:

  range of consistency scores for inclusion. If not specified, this
  defaults to `seq(from = 0.5, to = 1, by = 0.01)`.

- ncut:

  configurational n levels to simulate. Can be altered to give options
  for the range of minimum to maximum `ncut` value that the truth table
  yields, by naming the the truth table object (e.g. `truth`) and
  calling the minimum and maximum number of cases, using
  `ncut=min(truth$tt$n):max(truth$tt$n)` identified by the truth table.
  Default set to `ncut=2`.

- neg.out:

  \[from QCA package\] “Logical, use negation of outcome (ignored if
  data is a truth table object).” Default set to `neg.out=FALSE`.

- sim:

  number of simulations to run for each combination of parameters. The
  final number of simulations is `length(inclcut)*length(ncut)*sim*2`.
  Default set to `sim=10`.

- verbose:

  prints the system time used to run the simulation and the percent
  complete. Default set to `verbose=TRUE`.

## Value

Significance levels reached (.10,.05, .01, .001) when specifying a
combination of inclcut, ncut, and neg.out in a QCA model.

## Examples

``` r
qca.data <- rallies[,8:13]

if (FALSE) { # \dontrun{
brQCA(qca.data,outcome="P",ncut=5,sim=1)
} # }
```
