# Counterparty exposure modelling: Longstaff–Schwartz vs Tsitsiklis–Van Roy

Comparison of two regression-based valuation algorithms - **Longstaff–Schwartz (LSM)** and **Tsitsiklis–Van Roy (TVR)** - for computing counterparty credit exposure on a 10-year USD interest-rate portfolio consisting of a payer interest rate swap (IRS) and an Asian call option, both referencing the same simulated USD rate (Black–Scholes / GBM dynamics). Exposure is measured with the standard profiles - Expected (Positive) Exposure and the 2.5% / 97.5% quantiles of the mark-to-market distribution - and both algorithms are validated against independent benchmarks (a closed-form swap formula,
nested Monte Carlo for the option) and checked for convergence as the number of simulated paths grows.

All theory, derivations and discussion live in the notebook itself,
[`exposure_LSM_vs_TVR.ipynb`](exposure_LSM_vs_TVR.ipynb).

## Contents

The notebook is organized as follows:

1. **Mark-to-market (MtM) value** - definition of $V_t$, the quantity being estimated
2. **Exposure** - EFV, EE, ENE, and quantile (PFE) profiles
3. **Instruments** - the IRS and the Asian option
4. **Rate model** - GBM simulation of the USD rate
5. **Regression-based algorithms** - the general idea, then LSM and TVR
6. **Results** - exposure profiles for both instruments and the netted portfolio
7. **Validation** - LSM/TVR vs a closed-form formula (swap) and nested MC (option)
8. **Convergence** - RMSE vs benchmark as the number of paths grows

## Requirements

- Python 3.10+
- `numpy`, `matplotlib`, `scipy`

```bash
pip install numpy matplotlib scipy
```

## Usage

```bash
jupyter notebook exposure.ipynb
```

## References

- Longstaff, F. A., & Schwartz, E. S. (2001). Valuing American Options by Simulation: A Simple Least-Squares Approach. *The Review of Financial Studies*, 14(1), 113–147. https://doi.org/10.1093/rfs/14.1.113
- Tsitsiklis, J. N., & Van Roy, B. (1999). Optimal Stopping of Markov Processes: Hilbert Space Theory, Approximation Algorithms, and an Application to Pricing High-Dimensional Financial Derivatives. *IEEE Transactions on Automatic Control*, 44(10), 1840–1851. https://doi.org/10.1109/9.793723
