# 📊 Statistics & Probability Portfolio

A curated collection of three **independent, fully executed** projects from the
*Engineering Probability and Statistics* course at the **University of Tehran**
(School of Electrical and Computer Engineering) — covering statistical data
analysis, distribution recognition, stochastic modeling, and empirical
verification of fundamental laws.

> Each folder below is a **self-contained project** with its own detailed
> `README.md`, notebook, and dependency documentation.

---

## 🗂️ Projects

| Folder | Focus | Language |
|---|---|---|
| 📊 [`eps-statistical-distribution-analysis/`](eps-statistical-distribution-analysis/) | Statistical distribution analysis & recognition on the Titanic dataset + Monte-Carlo simulation and memorylessness | R · Plotly |
| 🎲 [`eps-random-variables-stochastic-models/`](eps-random-variables-stochastic-models/) | Sums of random variables (Gamma/Beta), covariance & autocorrelation, Markov belief model (WALL-E) | R · ggplot2 |
| 📈 [`eps-clt-and-benfords-law/`](eps-clt-and-benfords-law/) | Central Limit Theorem in practice + Benford's Law verification on real-world GDP data | R · ggplot2 |

---

## 🔍 At a Glance

- **eps-statistical-distribution-analysis** — Q–Q plot based recognition of the
  distributions underlying `Age`, `Fare`, and `ReactionTime`; joint
  probability reasoning under a limited testing budget; Poisson equivalence of
  exponential event counts; empirical demonstration of memorylessness.
- **eps-random-variables-stochastic-models** — simulation-verified Gamma and
  Beta distributions, hand-written correlation/autocorrelation analysis on
  real weather data, and a discrete Markov belief model for robot
  localization under sensor and motion noise.
- **eps-clt-and-benfords-law** — the CLT demonstrated on a skewed real dataset
  and three known parents, and Benford's first-digit law verified against
  1,704 real-world GDP observations.

## 🧾 Conventions

- Every notebook is committed **fully executed** — all plots, logs, and
  metrics are embedded and readable without re-running.
- Each project has its own `requirements.md` documenting the exact runtime
  and packages (R-kernel notebooks; no Python `requirements.txt` for R-only
  projects).
- Notebooks were developed for Google Colab; every README explains how to run
  in Colab or local Jupyter.

