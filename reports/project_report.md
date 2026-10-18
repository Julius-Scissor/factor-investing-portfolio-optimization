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

## 4. Data and Methodology

### 4.1 Stock Universe

The analysis considers five Indian-listed equities:

| Company | Yahoo Finance Ticker |
|---|---|
| Reliance Industries | `RELIANCE.NS` |
| Tata Consultancy Services | `TCS.NS` |
| Infosys | `INFY.NS` |
| HDFC Bank | `HDFCBANK.NS` |
| ICICI Bank | `ICICIBANK.NS` |

The selected universe includes companies from the energy, information technology, and financial services sectors. This provides some cross-sector exposure, although five stocks are not sufficient to represent the full Indian equity market.

### 4.2 Data Source and Preprocessing

Historical market data is retrieved using the Yahoo Finance interface through the Python `yfinance` library. Pandas is used to organize and process the resulting time series.

The project uses a historical study period spanning 2020 through 2025. Individual experiments may use different start dates, end dates, and training or evaluation windows depending on their objectives.

The preprocessing workflow includes aligning observations by date, handling missing values, and calculating returns from price series. Adjusted prices are used where specified by the relevant notebook.

Since historical data providers may revise their records, rerunning the notebooks at a later date may produce slightly different results.

### 4.3 Return and Risk Measurement

For a price series \(P_t\), the simple daily return is calculated as

\[
r_t = \frac{P_t}{P_{t-1}} - 1.
\]

For a portfolio with asset weights \(w_i\) and asset returns \(r_{i,t}\), the portfolio return is

\[
r_{p,t} = \sum_{i=1}^{N} w_i r_{i,t},
\]

provided the weights and returns are aligned for the same date.

The project evaluates portfolio performance using measures such as cumulative return, annualized return, volatility, Sharpe ratio, and maximum drawdown. These metrics describe different aspects of performance and should be interpreted together rather than in isolation.

### 4.4 Portfolio Construction

The project studies equal-weight allocations and optimization-based portfolios. Equal weighting provides a simple reference allocation, while optimization methods use estimated return and risk inputs to determine portfolio weights.

Mean-variance optimization evaluates allocations using expected returns and a covariance matrix. Long-only and position-limit constraints are considered in the constrained optimization experiments.

The resulting weights depend on the estimation window, covariance estimator, constraints, and assumptions used by the optimizer.

### 4.5 Factor Strategies

Two factor approaches are explored: momentum and low volatility.

The momentum strategy uses historical price behaviour to rank or select assets according to the signal defined in the factor-construction notebook. The low-volatility strategy uses historical volatility estimates to favour assets with lower measured variability.

The precise lookback windows, ranking rules, rebalancing logic, and execution timing are defined in the corresponding notebooks and should be reported from those implementations. Signals must be constructed using information available at the time of the simulated decision to reduce look-ahead bias.

### 4.6 Backtesting Design

The project uses several complementary evaluation designs:

- Historical strategy backtesting for comparing factor portfolios.
- A chronological training and test split for evaluating optimized allocations on later observations.
- Robustness checks that vary portfolio constraints and estimation assumptions.
- Walk-forward backtesting that repeatedly estimates portfolio weights using historical observations and evaluates subsequent returns.

Transaction costs are modeled in the relevant backtesting experiments. The results depend on the cost assumptions and turnover calculation used by each notebook.

### 4.7 Evaluation Principles

A fair comparison requires strategies to be evaluated over the same dates with consistent benchmark alignment, return definitions, and transaction-cost conventions.

Results from experiments with different evaluation windows are therefore presented separately. Out-of-sample performance is emphasized because in-sample optimization results can overstate how well a strategy performs on unseen data.


- How do rolling portfolio strategies behave when transaction costs are included?

