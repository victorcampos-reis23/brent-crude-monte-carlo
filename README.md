# Brent Crude Oil: Monte Carlo Risk & Pricing Simulator

This project implements a **Stochastic Risk Engine** to model future price trajectories for **Brent Crude Oil (BZ=F)** using the **Geometric Brownian Motion (GBM)** framework. It serves as a decision-support tool for energy risk management, bridging the gap between stochastic calculus and petroleum economics.

The goal is to demonstrate:
* **Real-world stochastic process simulation** using live energy market data.
* **Risk-neutral valuation** and uncertainty quantification.
* **Numerical approximation** of future asset prices via Monte Carlo iterations.
* **Petroleum Economics Metrics**: Identification of P10, P50, and P90 price scenarios for project stress-testing.

---

## Project Overview

* The **Brent Crude Oil** price is modeled using Geometric Brownian Motion (GBM) based on annualized historical volatility.
* A Monte Carlo engine generates 10,000 potential future trajectories.
* The model provides a statistical distribution of prices at a 1-year horizon, allowing analysts to move beyond static "Base Case" estimates to a probabilistic market outlook.

---

## Mathematical Framework

### 1. Geometric Brownian Motion (GBM)
Under the risk-neutral measure, the asset price follows the Stochastic Differential Equation (SDE):

$$dS_t = r S_t dt + \sigma S_t dW_t$$

Where:
* $S_t$ = Brent Crude price (USD/Bbl)
* $r$ = Risk-free rate
* $\sigma$ = Annualized historical volatility
* $W_t$ = Brownian motion

The exact discretized solution used for path generation is:

$$S_{t+\Delta t} = S_t \exp\left((r - 0.5\sigma^2)\Delta t + \sigma\sqrt{\Delta t} Z\right)$$

Where $Z \sim N(0,1)$.

### 2. Risk Metrics (P10, P50, P90)
In petroleum economics, we quantify uncertainty through percentiles:
* **P90 (Conservative)**: 90% probability that the price will stay above this level.
* **P50 (Base Case)**: The median expected price (50/50 scenario).
* **P10 (Optimistic)**: 10% probability that the price will exceed this level.

---

## Features

* **Real-Time Data**: Automated fetching of Brent Crude (`BZ=F`) futures via Yahoo Finance.
* **Dynamic Volatility**: Annualized log-return calculation for precise $\
