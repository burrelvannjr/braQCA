# `braQCA`: Bootstrapped robustness assessment for qualitative comparative analysis

<!-- badges: start -->
[![](https://www.r-pkg.org/badges/version/braQCA?color=green)](https://cran.r-project.org/package=braQCA)
[![](http://cranlogs.r-pkg.org/badges/grand-total/braQCA?color=blue)](https://cran.r-project.org/package=braQCA)
[![](http://cranlogs.r-pkg.org/badges/last-month/braQCA?color=blue)](https://cran.r-project.org/package=braQCA)
<!-- badges: end -->


## Overview

`braQCA` is an R package that provides bootstrapped robustness tools for Qualitative Comparative Analysis (QCA). QCA is a set-theoretic, case-oriented method widely used in political science, sociology, and comparative policy research to identify combinations of conditions sufficient or necessary for an outcome. A persistent challenge in QCA is that its truth table algorithm can return non-trivial solutions even when applied to purely random data — meaning researchers may inadvertently identify patterns that are artifacts of chance rather than genuine causal structures.

`braQCA` addresses this problem directly through two complementary tools:

- **`baQCA()`** — tests whether a completed QCA solution is robust to randomness by estimating the probability that the researcher's data and parameters would yield a non-trivial result by chance alone.
- **`brQCA()`** — provides data-driven recommendations for consistency score and configurational *n* thresholds needed to attain desired levels of statistical confidence in a given QCA application.

Together, these tools function as a hypothesis testing framework for QCA, producing output analogous to a *p*-value that researchers can use to assess and report the robustness of their findings.

The methodology is detailed in:

> Gibson, C. Ben and Burrel Vann Jr. 2025. "A Bootstrapped Robustness Assessment for Qualitative
Comparative Analysis." *Journal of Mathematical Sociology 40*(3): 147–174. [doi:10.1080/0022250X.2025.2496154](https://www.burrelvannjr.com/docs/gibson_and_vann_2025.pdf)



## Installation

---

Install the released version from CRAN:

```r
install.packages("braQCA")
```

Then load the package:

```r
library(braQCA)
```

`braQCA` depends on the [QCA](https://CRAN.R-project.org/package=QCA) package. If it is not yet installed, install it first:

```r
install.packages("QCA")
```



## Functions

---

| Function | Description |
|---|---|
| `baQCA()` | **Bootstrapped Assessment** — tests the robustness of a completed QCA model object to randomness, returning a probability (analogous to a *p*-value) and confidence interval |
| `brQCA()` | **Bootstrapped Recommendation** — scans combinations of consistency score (`inclcut`) and configurational *n* (`ncut`) thresholds, reporting which combinations attain standard significance levels (.10, .05, .01, .001) |
| `summary.baQCAtest()` | Summarizes the results of a `baQCA()` assessment |
| `sim.brQCA()` | Internal simulation engine used by `brQCA()` to calculate bootstrapped recommendations |
| `conf.table()` | Internal function that uses logistic regression to compute the output table for `brQCA()` |




## Examples

---

### Step 1 — Prepare data and run a QCA model

```r
library(QCA)
library(braQCA)

data(rallies)

# Select causal conditions
P <- rallies$P
R <- rallies$R
C <- rallies$C
U <- rallies$U

qca.data <- data.frame(P, R, C, U)
rownames(qca.data) <- rownames(rallies)

# Build truth table
truth <- truthTable(qca.data, outcome = "P", sort.by = "incl",
                    incl.cut1 = 0.7, show.cases = TRUE)
truth

# Minimize the truth table
mod1 <- minimize(truth, details = TRUE, show.cases = TRUE)
mod1
```

### Step 2 — Bootstrapped Assessment (`baQCA`)

```r
# Test robustness of the solution (use sim=2000 for production; sim=5 for quick testing)
baQCA(mod1, sim = 5)
```

The function returns the estimated probability that the data and chosen parameters would yield a random result, along with a confidence interval. A low value (e.g., < .05) indicates the solution is unlikely to be an artifact of chance.

### Step 3 — Bootstrapped Recommendation (`brQCA`)

```r
qca.data <- rallies[, 8:13]

# Get parameter recommendations (use higher sim for production)
brQCA(qca.data, outcome = "P", ncut = 5, sim = 1)
```

This returns a table showing which combinations of `inclcut` and `ncut` achieve significance thresholds of .10, .05, .01, and .001 — helping researchers select defensible parameters before finalizing their QCA model.





## Included Datasets

---

### `rallies` — McVeigh et al. (2014) Tea Party Data

This dataset is an abbreviated version of the data used by McVeigh et al. (2014), covering all **67 counties in Florida**, drawn from the American Community Survey (2005–2009). It is the primary demonstration dataset for `braQCA`.

**Dimensions:** 67 observations × 13 variables

| Variable | Type | Description |
|---|---|---|
| `tprallies` | Continuous | Number of Tea Party rallies in county, 2009–2010 |
| `reppct2008` | Continuous | Percent voting Republican (McCain) in 2008 |
| `dempct2008` | Continuous | Percent voting Democrat (Obama) in 2008 |
| `pctBA25` | Continuous | Percent of residents aged 25+ with a bachelor's degree |
| `pctunemp` | Continuous | Percent unemployed |
| `pctevang` | Continuous | Percent belonging to an Evangelical denomination |
| `pctblack` | Continuous | Percent identifying as Black |
| `P` | Binary | `1` if county had at least one Tea Party rally; `0` otherwise |
| `R` | Binary | `1` if county majority voted Republican in 2008; `0` otherwise |
| `C` | Binary | `1` if percent with bachelor's degree was at or above Florida average; `0` otherwise |
| `U` | Binary | `1` if percent unemployed was at or above Florida average; `0` otherwise |
| `E` | Binary | `1` if percent Evangelical was at or above Florida average; `0` otherwise |
| `B` | Binary | `1` if percent Black was at or above Florida average; `0` otherwise |






## Dependencies

---

`braQCA` imports from the `QCA` package and uses `dplyr`, `stats`, and related utilities for simulation and table construction.

