# ILI Effect Size Framework

Code and data for the empirical illustration of the article:

> Luo, X., Liu, Y., Liu, H., & Bringmann, L. F. *Beyond Pre-Post
> Comparisons: A Comprehensive Effect Size Framework for Intensive
> Longitudinal Interventions via Time-Varying Modeling.*

The article proposes a comprehensive effect size framework for ILIs, 
built on Bayesian multilevel time-varying autoregressive (TV-AR) models 
within the generalized additive mixed model (GAMM) approach. 
The framework organizes effect sizes along four dimensions: 
(a) subject level (population-average, individual-specific, and between-group), 
(b) parameter type (mean level, autoregressive coefficient, and variance), 
(c) temporal scale (integrated over a phase, evaluated at each time point), and 
(d) study phase (active intervention, post-intervention decay). 

## Contents

| File | Description |
|---|---|
| `tutorial.Rmd` / `tutorial.html` | Step-by-step tutorial on the effect size framework, applied to the simulated dataset (the analysis reported in the article's main text) |
| `complete_analysis_code.Rmd` / `complete_analysis_code.html` | Complete code of all analyses: the empirical-data analysis, the generation of the simulated dataset, and the simulated-data analysis |
| `empirical_data.csv` | Prepared empirical dataset (123 participants; long format: `id`, `group`, `day`, `beep`, `t`, `phase`, `value`) |
| `simulated_data.csv` | Simulated dataset generated from the empirical posterior (150 participants per group; same format) |
| `Supplement_DecayEffectSizes.pdf` | Definitions of the post-intervention decay effect sizes (supplemental material) |

The rendered HTML files show all code together with the results and can
be read without running anything.

## Reproducing the analyses

Both `.Rmd` files are self-contained. Place them in one folder together
with the two data files and knit them in R. Requirements:

- R with the packages `cmdstanr`, `posterior`, `mgcv`, `dplyr`,
  `tidyr`, `purrr`, `tibble`, `ggplot2`, `knitr`, `rmarkdown`, and
  `prettydoc`
- CmdStan installed via `cmdstanr::install_cmdstan()`

Note that a full run fits eight Bayesian multilevel models (two groups
by two phases, for the empirical and the simulated data) and can take
one to two days. Finished model fits are cached on disk, so an
interrupted run can be resumed and later knits re-use the fits.
