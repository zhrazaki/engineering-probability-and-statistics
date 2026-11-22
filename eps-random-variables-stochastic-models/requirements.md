# Environment & Dependencies — eps-random-variables-stochastic-models

This is an **R**-kernel notebook. There is no `requirements.txt` (Python-only
convention); the environment is documented here instead.

## Runtime

- **R** ≥ 4.0 (developed on Google Colab's R runtime)
- **Jupyter Notebook** with the **IRkernel** (kernel name: `ir`), or
  **Google Colab** with the R runtime selected.

## R Packages

| Package | Used for | Install |
|---|---|---|
| `dplyr` | data manipulation (`mutate`, `%>%`) | `install.packages("dplyr")` |
| `ggplot2` | all static visualizations | `install.packages("ggplot2")` |
| `magrittr` | pipe operator (`%>%`) | `install.packages("magrittr")` |

The notebook installs these in its setup cells, so no manual installation is
required before running.

## Data

No external datasets are needed:

- Question 1 (Gamma/Beta parts) is fully Monte Carlo simulated.
- The covariance part uses `airquality`, which ships with base R.

## Reproducibility Notes

- The notebook is committed **fully executed**; all figures and outputs are
  embedded, so it can be read without re-running.
- Colab execution metadata has been removed from the notebook.
