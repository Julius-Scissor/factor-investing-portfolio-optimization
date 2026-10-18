# Factor Investing and Portfolio Optimization in Indian Equities

## Abstract

This project investigates factor-based investing and portfolio optimization using a selected universe of Indian equities. The analysis combines historical stock-return and risk measurement, portfolio diversification, mean-variance optimization, momentum and low-volatility strategies, constrained portfolio construction, and walk-forward backtesting.

The project is implemented in Python using a sequence of Jupyter notebooks. It evaluates how portfolio construction methods behave under different assumptions and emphasizes the importance of out-of-sample testing, transaction costs, and estimation uncertainty.

The objective is not to identify a universally optimal investment strategy, but to study the trade-offs between return, risk, diversification, and the sensitivity of optimized portfolios to their inputs.

## 1. Introduction

Portfolio construction is a central problem in quantitative finance. Investors must allocate capital across assets while balancing expected returns, volatility, diversification, and practical trading constraints.

Modern Portfolio Theory provides a mathematical framework for analyzing the relationship between portfolio risk and expected return. However, portfolios optimized using historical estimates may be sensitive to estimation errors. A strategy that performs well in a training sample may not retain its advantage in unseen data.

Factor investing offers another approach by constructing portfolios according to systematic characteristics or signals. This project examines momentum and low-volatility strategies alongside equal-weight portfolios and optimization-based allocations.

The analysis focuses on five Indian equities and uses historical data to investigate how these approaches compare across different evaluation setups.

## 2. Research Objectives

The main objectives are:

1. Analyze historical stock performance and risk.
2. Examine portfolio diversification and the relationship between risk and return.
3. Construct and evaluate momentum and low-volatility strategies.
4. Apply mean-variance portfolio optimization under allocation constraints.
5. Investigate sensitivity to covariance estimates, expected-return windows, and position limits.
6. Evaluate strategies using chronological out-of-sample and walk-forward backtesting.
7. Discuss the limitations of historical portfolio simulations.

## 3. Research Questions

This study addresses the following questions:

- How do momentum and low-volatility strategies compare with equal-weight portfolios in the selected sample?
- Does mean-variance optimization improve out-of-sample performance relative to simpler allocation methods?
- How sensitive are optimized portfolio weights to changes in estimation assumptions?
- How do rolling portfolio strategies behave when transaction costs are included?

