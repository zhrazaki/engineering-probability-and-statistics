# Random Variables & Stochastic Models

Simulation-based study of sums of random variables, ratio distributions,
covariance and dependence in real data, and a discrete Markov belief model
for robot localization.

## Academic Context

- **Course:** Engineering Probability and Statistics (EPS)
- **Institution:** School of Electrical and Computer Engineering, University of Tehran
- **Instructors:** Dr. Bahrak, Dr. Vahabie
- **Deliverable:** Computer Assignment 5 (CA5), implemented as a single
  R-kernel Jupyter notebook (`CA5.ipynb`)

## Project Overview

The notebook is organized around two questions:

1. **Sums and ratios of random variables.** A company's weekly loss from
   product returns is modeled as a sum of i.i.d. exponential random
   variables; the distribution of the loss, the share of one product in the
   total loss, and their theoretical counterparts (Gamma and Beta) are
   verified by simulation. Covariance and dependence are then explored on
   the built-in `airquality` dataset.
2. **Markov model for robot localization.** WALL-E moves through a walled
   grid map; a recursive belief update over noisy sensor readings and
   unreliable movement is implemented and evaluated against the robot's
   true position.

## Contents

### Question 1 (25 pts) — Sums of Random Variables, Covariance

| Task | Topic |
|---|---|
| 1–5 | Weekly loss `D` as a sum of 7 i.i.d. `Exp(λ = 0.01)`; histogram, density, and theoretical **Gamma(shape = 7, rate = 0.01)** PDF; mean and variance (simulation vs. theory) |
| 6–8 | Share of product `a` in the weekly loss → **Beta(7, 7)**; simulated vs. theoretical mean/variance; Beta PDF vs. histogram |
| 9–10 | The same ratio for a **single day** → **Beta(1, 1)** (uniform); verified by simulation and theory |
| 11+ | `airquality` dataset: temperature scatter, custom `Calculate_Correlation()` (Pearson correlation from covariance), lag-1 correlation of daily temperature, and autocorrelation up to lag 100 |

### Question 2 (25 pts) — WALL-E Localization (Markov model)

| Task | Topic |
|---|---|
| 1–2 | Grid map, movement model with 80/20 intended-vs-actual direction probabilities |
| 3–4 | Observation model `P(E_t | X_t)` for 10%-error wall sensors; transition function `P(X_t | X_{t-1})` |
| 5 | Recursive belief update `P(X_t | E_{1:t})` with normalization (`model()` function) |
| 8 | Evaluation: `plot_belief_maxima()` and `plot_belief_accuracy()` against the true trajectory over 300 moves |

## Mathematical and Statistical Methods

- Distribution of a sum of i.i.d. exponentials: **Gamma** with shape = number
  of days, verified against 100,000 simulated samples.
- Ratio of two Gamma variables: **Beta(α, β)** with α = β = 7 (weekly) and
  α = β = 1 (daily, i.e. Uniform); closed-form mean and variance compared
  with simulated values.
- Covariance and Pearson correlation implemented from the definition
  (`cov(X, Y) / sqrt(var(X) var(Y))`) and applied to lagged temperature series
  (autocorrelation analysis).
- Discrete Markov model: recursive Bayesian filtering
  `belief_t ∝ P(E_t | X_t) · Σ P(X_t | X_{t-1}) belief_{t-1}` with per-step
  normalization; accuracy evaluation against the hidden true state.

## Technologies and Tools

- **Language:** R (R kernel in Jupyter/Colab)
- **Packages:** `dplyr`, `ggplot2`, `magrittr` (pipe operator `%>%`)
- **Notebook:** Jupyter Notebook / Google Colab

## Repository Structure

```text
eps-random-variables-stochastic-models/
├── README.md
├── CA5.ipynb          # fully executed notebook with all outputs
└── requirements.md    # environment and dependency instructions
```

## How to Run

### Google Colab

1. Upload `CA5.ipynb` to Colab and switch the runtime to **R**.
2. Run all cells. Setup cells install `dplyr`, `ggplot2`, and `magrittr`.
3. No external data files are required: Question 1 is fully simulated, and
   Question 1's covariance part uses R's built-in `airquality` dataset.

### Local Jupyter

```bash
R -e "install.packages(c('IRkernel','dplyr','ggplot2','magrittr')); IRkernel::inst()"
jupyter notebook CA5.ipynb
```

See `requirements.md` for details.

## Dependencies

Documented in [`requirements.md`](requirements.md). In short: R with the
`IRkernel`, plus `dplyr`, `ggplot2`, and `magrittr`; no external datasets.

## Results and Key Findings

All findings below are taken from the executed notebook.

- **Gamma verification:** the simulated weekly-loss distribution
  (100,000 samples of the sum of 7 `Exp(0.01)` variables) matches the
  theoretical `Gamma(shape = 7, rate = 0.01)` density overlaid in the plots.
- **Beta(7, 7):** the weekly loss share `D_A / (D_A + D_B)` has simulated
  mean/variance consistent with the closed-form
  `α/(α+β)` and `αβ/((α+β)²(α+β+1))` for `α = β = 7`, and the Beta PDF matches
  the simulated histogram.
- **Beta(1, 1):** for a single day the ratio's simulated mean is 0.5 and the
  theoretical calculation gives the **Uniform(0, 1)** distribution
  (`Beta(1, 1)`), matching the simulation.
- **Temperature dependence:** lag-1 correlation of daily temperature is
  strongly positive, and the autocorrelation decays as the lag increases
  (computed up to lag 100 with the hand-written correlation function).
- **Localization:** the belief update tracks the robot's true position under
  10% sensor error and 20% wrong-move noise; the belief-maximum and accuracy
  plots show the model recovering the correct cell after ambiguous
  observations.

## Attribution

Assignment statements, question narratives, and point breakdowns are part of
the course material for the EPS assignment; the completed implementations,
theory answers, and simulations are the student's work for CA5.
