# Statistical Distribution Analysis — Titanic Passenger Data

Analysis of the statistical distributions underlying three passenger features of
the Titanic dataset (`Age`, `Fare`, `ReactionTime`), followed by a Monte Carlo
study of exponentially distributed response times and the memoryless property.

## Academic Context

- **Course:** Engineering Probability and Statistics (EPS)
- **Institution:** School of Electrical and Computer Engineering, University of Tehran
- **Instructors:** Dr. Bahrak, Dr. Vahabie
- **Deliverable:** Computer Assignment 4 (CA4), implemented as a single R-kernel
  Jupyter notebook (`CA4.ipynb`)

## Project Overview

The notebook is organized around two questions:

1. **Statistical distribution analysis of the Titanic dataset.** Exploratory
   analysis of the joint and marginal distributions of three passenger
   features, identification of candidate probability distributions via
   Q–Q plots, parameter estimation, and probabilistic reasoning under a
   limited testing budget.
2. **Monte Carlo simulation and memorylessness.** Simulation of event counts
   in fixed time windows when inter-event times are exponential, comparison
   with the Poisson distribution, and an experimental verification of the
   memoryless property.

## Contents

### Question 1 — Statistical Distribution Analysis (Titanic dataset)

| Part | Topic |
|---|---|
| Part 1 | EDA and visualization of `Age`, `Fare`, `ReactionTime` |
| Part 2 | `marginalize()` implementation; bar plots vs. density histograms |
| Part 3 | Q–Q plots against Normal, Log-normal, and Exponential candidates |
| Part 4 | Parameter estimation; joint probability of recalled feature ranges; expected number of matching passengers among 1309 |
| Part 5 | Binomial model `X ~ Binomial(N, p_joint)`; exact `P(X ≤ 19)`; Normal approximation and its correction |

### Question 2 — Monte Carlo Simulation & Memorylessness

| Part | Topic |
|---|---|
| Part 1 | `count_from_exponential()`: event counts per fixed window from exponential inter-event times (with correct handling of samples overshooting the window) |
| Part 2 | Comparison of simulated counts with Poisson (summary statistics, Q–Q plot); empirical and theoretical demonstration of memorylessness |

## Mathematical and Statistical Methods

- Marginalization of a joint empirical distribution over binned features.
- Q–Q plots for judging distributional fit against Normal, Log-normal, and
  Exponential families.
- Method-of-moments parameter estimates: mean/SD for Normal; mean/log-SD of
  `log(Fare)` for Log-normal; `1/mean` for Exponential rate.
- Joint probability under an independence assumption, multiplied by the
  population size (1309) to obtain an expected count.
- Exact binomial probability `pbinom`, Normal approximation to the binomial,
  and the continuity correction (`+ 0.5`).
- Derivation that event counts from exponential inter-arrival times follow a
  Poisson distribution; comparison via summary statistics and Q–Q plots.
- Conditional probability identity `P(X > s + t | X > s) = P(X > t)` for the
  exponential distribution.

## Technologies and Tools

- **Language:** R (R kernel in Jupyter/Colab)
- **Packages:** `plotly` (interactive figures), `viridisLite` (palettes)
- **Notebook:** Jupyter Notebook / Google Colab

## Repository Structure

```text
eps-statistical-distribution-analysis/
├── README.md
├── CA4.ipynb          # fully executed notebook with all outputs
└── requirements.md    # environment and dependency instructions
```

The notebook is self-contained; all figures are embedded in the notebook
outputs. Histogram PNGs written by the code (`hist_*.png`) are regenerated
when the notebook is run and are not stored in the repository.

## How to Run

### Dataset notice

The notebook expects `data.csv` in its working directory
(`read.csv("data.csv", header = TRUE)`). The dataset (1309 Titanic
passengers with `Age`, `Fare`, `ReactionTime`) is **not included** in this
repository; place `data.csv` next to the notebook before running.

### Google Colab

1. Upload `CA4.ipynb` to Colab and switch the runtime to **R**
   (Runtime → Change runtime type → R).
2. Upload `data.csv` to the session storage.
3. Run all cells. The first cell installs `plotly`.

### Local Jupyter

```bash
# R ≥ 4.x with the IRkernel
R -e "install.packages('IRkernel'); IRkernel::inst()"
jupyter notebook CA4.ipynb
```

See `requirements.md` for the full dependency list.

## Dependencies

Documented in [`requirements.md`](requirements.md). In short: R with the
`IRkernel`, plus the `plotly` and `viridisLite` packages.

## Results and Key Findings

All findings below are taken from the executed notebook.

- **Fitted distributions (Part 3–4):** `Age` is modeled as Normal (with NA
  handling), `Fare` as Log-normal (excluding zero fares, which otherwise
  produce `NaN` in the log-transform), and `ReactionTime` as Exponential
  (`rate = 1/mean`).
- **Expected match count (Part 4):** using the recalled ranges
  `Age ∈ [19, 25]`, `Fare ∈ [30, 100]`, `ReactionTime ∈ [0.05, 0.8]` and an
  independence assumption, the notebook computes the joint probability and
  the expected number of matching passengers among 1309.
- **Binomial analysis (Part 5):** with `X ~ Binomial(N, p_joint)`, the exact
  `P(X ≤ 19)` is computed via `pbinom`; the plain Normal approximation
  underestimates this probability, and adding the **continuity correction**
  (`pnorm(19 + 0.5, …)`) brings the approximation close to the exact value.
- **Poisson equivalence (Q2, Part 1):** counts produced by
  `count_from_exponential()` match a Poisson distribution in summary
  statistics, and the Q–Q plot of simulated counts vs. Poisson quantiles
  falls on a straight line.
- **Memorylessness (Q2, Part 2):** the empirical estimates of
  `P(X > s + t | X > s)` and `P(X > t)` agree, matching the theoretical
  identity for the exponential distribution.

## Attribution

Assignment statements, question narratives, and starter code fragments are
part of the course material for the EPS assignment; the analysis, completed
implementations, and simulations are the student's work for CA4.
