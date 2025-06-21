# Markov Switching Dynamic Nelson-Siegel (MSDNS) Model

## Overview

This project implements the **Markov Switching Dynamic Nelson-Siegel (MSDNS)** model for yield curve estimation and forecasting, as described in Hevia et al. (2012, 2014). The MSDNS model extends the classic Nelson-Siegel approach by allowing all parameters to switch across different economic regimes, which are modeled as a Markov chain. This enables the model to capture structural changes in yield curve dynamics, such as those caused by business cycles.

---

## Features

- **Regime Switching:** Models different economic environments (e.g., expansion/recession) via a Markov process.
- **Dynamic Factors:** Models level, slope, and curvature factors with regime-dependent dynamics.
- **Efficient Filtering:** Uses an approximate Bayesian filter to maintain tractability.
- **Robust Optimization:** Multi-stage parameter estimation (Simulated Annealing, Nelder-Mead, BFGS).
- **Probabilistic Forecasting:** Monte Carlo simulation for full predictive distributions.
- **Comprehensive Diagnostics:** Summarizes regime parameters, transition probabilities, and expected durations.

---

## Model Specification

### Observation Equation

$$
y_t = \Lambda_{x_t} f_t + \varepsilon_{x_t, t}
$$

- $y_t$: Vector of observed yields at time $t$
- $\Lambda_{x_t}$: Nelson-Siegel loading matrix (regime-dependent)
- $f_t$: Latent factors (level, slope, curvature)
- $\varepsilon_{x_t, t}$: Observation noise

### State Equation

$$
f_t = \mu_{x_t} + A_{x_t} f_{t-1} + \eta_{x_t, t}
$$

- $\mu_{x_t}$: Regime-specific drift
- $A_{x_t}$: Regime-specific autoregressive matrix
- $\eta_{x_t, t}$: State innovation noise

### Nelson-Siegel Loadings

For each maturity $\tau$ and regime $j$:

- Level: $1$
- Slope: $\frac{1 - e^{-\lambda_j \tau}}{\lambda_j \tau}$
- Curvature: $\frac{1 - e^{-\lambda_j \tau}}{\lambda_j \tau} - e^{-\lambda_j \tau}$

---

## Installation
- git clone https://github.com/x-senpai-x/yieldCurveEstimation
- cd msdns-model 

## Notes

- The implementation is modular and can be extended to more than two regimes or additional factors.
- Parameter bounds and initialization strategies are based on econometric best practices for stability and identification.
- The code is suitable for research, teaching, and production applications in finance and macroeconomics.

## References

1. Hevia, C., Gonzalez-Rozada, M., Sola, M., & Spagnolo, F. (2012). *Estimating and Forecasting the Yield Curve Using a Markov Switching Dynamic Nelson and Siegel Model*. Journal of Forecasting, 31(1), 57-79.
2. Diebold, F.X., & Li, C. (2006). *Forecasting the Term Structure of Government Bond Yields*. Journal of Econometrics, 130(2), 337-364.