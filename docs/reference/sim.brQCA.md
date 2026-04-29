# Simulation Application

Internal function to calculate the Bootstrapped Recommendation.

## Usage

``` r
sim.brQCA(
  qca.data,
  outcome = "OUT",
  conditions = c(""),
  sim = 10,
  ncut = 2,
  type = "crisp",
  inclcut = "",
  neg.out = FALSE,
  verbose = TRUE
)
```

## Arguments

- qca.data:

  the data frame of causal conditions.

- outcome:

  the outcome variable (object name) in the QCA data frame of causal
  conditions; `"OUT"` is the outcome variable for an application of QCA.
  Default set to `outcome="OUT"`.

- conditions:

  a set of causal conditions. Default set to `conditions=c("")`

- sim:

  number of simulations to run. Default set to `sim=10`.

- ncut:

  configurational n levels for inclusion. Default set to `ncut=2`.

- type:

  type of QCA application, `"crisp"` or `"fuzzy"` sets. Default set to
  `type = "crisp"`.

- inclcut:

  minimum sufficiency score for inclusion. Default set to `inclcut=""`.

- neg.out:

  \[from QCA package\] “Logical, use negation of outcome (ignored if
  data is a truth table object).” Default set to `neg.out=FALSE`.

- verbose:

  prints the system time used to run the simulation and the percent
  complete. Default set to `verbose=TRUE`.

## Value

Simulation information later passed on to conf.table.
