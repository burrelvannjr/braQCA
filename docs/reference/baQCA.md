# Boostrapped Assessment

This function performs the the Bootstrapped Assessment for QCA (baQCA)
on a given QCA model object.

## Usage

``` r
baQCA(
  mod,
  sim = 2000,
  all = TRUE,
  include = c(""),
  row.dom = FALSE,
  omit = c(),
  dir.exp = c()
)
```

## Arguments

- mod:

  name of the QCA model object – the minimization of the truth table.

- sim:

  the number of simulations the baQCA function should run. Default set
  to `sim=2000`.

- all:

  logical, whether or not causal conditions AND outcome should be
  resampled (with replacement). Default set to `all=TRUE`.

- include:

  \[from QCA package\] “A vector of additional output function values to
  be included in the minimization.” Default set to `include=c("")`.

- row.dom:

  \[from QCA package\] “Logical, impose row dominance as constraint on
  solution to eliminate dominated inessential prime implicants.” Default
  set to `FALSE`.

- omit:

  \[from QCA package\] “A vector of configuration index values or matrix
  of configurations to be omitted from minimization.” Default set to
  `omit=c()`.

- dir.exp:

  \[from QCA package\] “A vector of directional expectations for
  deriving intermediate solutions.” Default set to `dir.exp=c()`.

## Value

This function returns a value which is the probability of a random QCA
result (e.g. a result from random data) given the parameters set by the
researcher in the model (configurational n threshold, consistency score
threshold, etc), and a confidence interval around this value. This value
is interpreted similarly to a p-value."

## Examples

``` r
qca.data <- rallies[,8:13]
rownames(qca.data)<-rownames(rallies)
truth<-QCA::truthTable(qca.data,outcome="P",sort.by="incl",incl.cut1=0.85,n.cut=1,show.cases=TRUE)
mod1 <- QCA::minimize(truth,details=TRUE,show.cases=TRUE)
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().

summary(baQCA(mod1,sim=1))
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#>                Length Class  Mode   
#> call           3      -none- call   
#> total.sims     1      -none- numeric
#> total.ci.boots 1      -none- numeric
#> result         3      -none- numeric
```
