# Dynamic Portfolio Management with LSTM and Stress Testing

## Overview

This project studies the construction of a dynamic minimum-variance portfolio using LSTM-based forecasts of the covariance matrix between two financial assets.

The analysis combines return preprocessing, covariance forecasting with a recurrent neural network, daily portfolio rebalancing, benchmark comparison with a rolling historical covariance approach, and portfolio risk assessment through Value at Risk (VaR), Expected Shortfall (ES), stress testing, and backtesting.

Conducted in the context of the *AI and Finance* course, the project brings together portfolio allocation, time-series modeling, and quantitative risk analysis within a unified empirical framework.

## Data and assets

The analysis is based on two financial assets:
- **TSLA**
- **SPY**

Daily market data are collected from Yahoo Finance. Simple daily returns are then computed and divided into:
- a **training period** covering **2010–2023**
- a **test period** covering **2024–2025**

## Methodology

The project is organized around four main stages:

1. **Data collection and preparation**  
   Historical prices are retrieved, cleaned, and transformed into daily return series.

2. **Covariance forecasting**  
   An LSTM model is trained on rolling sequences of past returns in order to produce one-step-ahead covariance estimates.

3. **Portfolio construction**  
   The predicted covariance matrix is used to compute a dynamic long-only minimum-variance portfolio, updated day by day over the out-of-sample period.

4. **Risk measurement and backtesting**  
   Portfolio risk is evaluated using dynamic VaR and ES measures under both standard and stressed conditions, and the resulting estimators are assessed on the test period.

## LSTM-based covariance modeling

The covariance forecasting component is implemented in PyTorch and relies on sequential return information.

The notebook develops a recurrent neural network approach designed to capture the short-term dynamics of dependence between the two assets and to generate daily covariance forecasts used for portfolio allocation.

## Portfolio construction

Using the predicted covariance matrix, the project computes a long-only minimum-variance allocation subject to standard portfolio constraints.

The allocation is updated dynamically through time, and the notebook tracks:
- portfolio value
- asset weights
- capital allocated to each asset
- portfolio rebalancing over time

## Benchmark comparison

The LSTM-based strategy is compared with a benchmark based on rolling historical covariance estimation.

This comparison makes it possible to evaluate the contribution of a predictive covariance framework relative to a more standard backward-looking allocation rule.

## Risk metrics

The project evaluates portfolio risk through:
- **Value at Risk (VaR)**
- **Expected Shortfall (ES)**
- **stress scenario analysis**
- **backtesting of risk estimates**

The notebook includes both standard and stress-adjusted risk measures in order to compare their behaviour over the out-of-sample period.

## Results

The project reports out-of-sample portfolio results over the 2024–2025 test period and compares the LSTM-based allocation with a rolling-window benchmark.

Overall, the notebook indicates a positive out-of-sample performance for the LSTM-based portfolio and a more conservative profile for stress-adjusted risk measures.

