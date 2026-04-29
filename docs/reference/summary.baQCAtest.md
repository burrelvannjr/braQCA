# Summarize Results of baQCA

Displays results of baQCA.

## Usage

``` r
# S3 method for class 'baQCAtest'
summary(object, ...)
```

## Arguments

- object:

  Object returned by [`baQCA`](baQCA.md).

- ...:

  Additional parameters to pass on.

## Value

Matrix of values for percent of simulations returning result from random
data, along with confidence interval.

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

test <- baQCA(mod1,sim=1) 
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
#> Warning: Function writePrimeimp() is deprecated, use writePIs().
summary(test)
#>                Length Class  Mode   
#> call           3      -none- call   
#> total.sims     1      -none- numeric
#> total.ci.boots 1      -none- numeric
#> result         3      -none- numeric
```
