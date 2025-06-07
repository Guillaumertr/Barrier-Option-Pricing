# Barrier Option Pricing – Advanced Monte Carlo Simulation

This notebook implements a robust and accurate pricing method for **barrier options** using **Monte Carlo simulation** combined with a probabilistic modeling of path extrema.

---

## Motivation

Barrier options are exotic derivatives whose payoff depends not only on the final price of the underlying asset, but also on whether the asset has breached a certain barrier level during its life. Examples include:
- **Up-and-Out Call**
- **Down-and-Out Put**
- ... and their "In" counterparts.

A naïve Monte Carlo approach would simulate standard asset paths and simply check, at each discrete time step, whether the barrier has been breached. However, this method is flawed:

> **Key Insight:**  
> Due to discrete time steps, a path that should have crossed the barrier might not be detected as such — especially when the crossing is small or occurs between two time steps.

This notebook avoids that inaccuracy by:
- Simulating the **joint law** of the asset and its **running maximum (or minimum)** using known properties of **Brownian motion with drift**.
- Applying **analytical formulas** for the probability of crossing the barrier within a time interval, enabling far more precise estimation of the crossing behavior.

This approach yields **much more reliable pricing**, especially for tight barriers or short maturities where discrete sampling fails.

---

## Features

- Asset modeled under risk-neutral **Geometric Brownian Motion (GBM)**.
- Vectorized Monte Carlo simulation using NumPy.
- Joint simulation of terminal price and extrema (max/min).
- Implementation of both **up** and **down** barriers.
- Confidence intervals computed using Central Limit Theorem.

---

## Experiments

- Pricing for different barrier levels
- Comparing the result with standard European call for intuition
- Studying convergence and variance reduction

---

## Requirements

- Python 3.8+
- `numpy`, `matplotlib`, `scipy`, `tqdm`

---

## Insights

- Illustrates how standard Monte Carlo methods adapt to path-dependent options
- Shows how hitting a barrier can drastically alter the option's value
- Builds intuition on Greeks sensitivity near the barrier

---

## Use Case

Perfect for:
- Quantitative finance students exploring path-dependent derivatives
- Practitioners needing a clean implementation of barrier pricing
- Educational demonstrations of exotic option behavior

---

## References

- Pages, G. *Introduction to Numerical Probabilities for Finance*

## Author

Guillaume Routier  
MSc Probabilité & Finance – École Polytechnique & Sorbonne Université  
[Contact me on LinkedIn](https://www.linkedin.com/in/guillaume-routier/)

---

## Disclaimer

These notebooks are for educational and demonstrative purposes only. They do not constitute financial advice.
