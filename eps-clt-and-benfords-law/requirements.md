# Environment & Dependencies — eps-clt-and-benfords-law

This is an **R**-kernel notebook. There is no `requirements.txt` (Python-only
convention); the environment is documented here instead.

## Runtime

- **R** ≥ 4.0 (developed on Google Colab's R runtime)
- **Jupyter Notebook** with the **IRkernel** (kernel name: `ir`), or
  **Google Colab** with the R runtime selected.

## R Packages

| Package | Used for | Install |
|---|---|---|
| `ggplot2` | all visualizations (histograms, Normal overlays, Benford comparison) | `install.packages("ggplot2")` |
| `tidyr` | reshaping data for grouped bar plots | `install.packages("tidyr")` |
| `gapminder` | real-world country-year data (population, GDP per capita) | `install.packages("gapminder")` |

The notebook installs `gapminder` in its setup cell.

## Data

No external data files are needed:

- The CLT sections use simulated data (seeded where reproducibility matters)
  and a watch-time dataset defined/generated inside the notebook.
- The Benford section uses the `gapminder` package dataset (1,704 rows).

## Reproducibility Notes

- The notebook is committed **fully executed**; all figures and outputs are
  embedded, so it can be read without re-running.
- Colab execution metadata has been removed from the notebook.
