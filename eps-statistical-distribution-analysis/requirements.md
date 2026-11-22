# Environment & Dependencies — eps-statistical-distribution-analysis

This is an **R**-kernel notebook. There is no `requirements.txt` (Python-only
convention); the environment is documented here instead.

## Runtime

- **R** ≥ 4.0 (developed on Google Colab's R runtime)
- **Jupyter Notebook** with the **IRkernel** (kernel name: `ir`), or
  **Google Colab** with the R runtime selected.

## R Packages

| Package | Used for | Install |
|---|---|---|
| `plotly` | interactive figures (bar plots, histograms, Q–Q plots) | `install.packages("plotly")` |
| `viridisLite` | color palettes used with plotly | installed automatically as a `plotly` dependency |

The notebook calls `install.packages("plotly")` in its setup cell, so no
manual installation is required before running.

## Installation (local Jupyter)

```r
install.packages(c("IRkernel", "plotly", "viridisLite"))
IRkernel::inst()   # registers the R kernel with Jupyter
```

## Data

`CA4.ipynb` reads `data.csv` from its working directory. This CSV is not
redistributed with the repository; supply it before executing the notebook
(see the "How to Run" section of the README).

## Reproducibility Notes

- The notebook is committed **fully executed**; all figures and outputs are
  embedded, so it can be read without re-running.
- Random parts use explicit seeds where reproducibility matters
  (`set.seed(42)` for the binomial simulation).
- Colab execution metadata has been removed from the notebook.
