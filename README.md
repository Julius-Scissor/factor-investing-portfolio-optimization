# Factor Investing and Portfolio Optimization in Indian Equities

A quantitative finance research project exploring factor-based investing, portfolio optimization, risk analysis, and walk-forward backtesting using Python.

## Overview

This project investigates how different portfolio construction techniques perform on a selected universe of Indian equities. It combines classical portfolio theory with factor strategies and out-of-sample evaluation.

The goal is to understand the trade-offs between return, volatility, diversification, estimation risk, and portfolio constraints.

## Research Universe

The analysis focuses on five Indian-listed stocks:

- Reliance Industries (`RELIANCE.NS`)
- Tata Consultancy Services (`TCS.NS`)
- Infosys (`INFY.NS`)
- HDFC Bank (`HDFCBANK.NS`)
- ICICI Bank (`ICICIBANK.NS`)

Historical market data is retrieved using Python and Yahoo Finance.

## Project Roadmap

1. Data collection and preprocessing
2. Stock performance and risk analysis
3. Portfolio construction and diversification
4. Modern Portfolio Theory
5. Efficient frontier and Monte Carlo optimization
6. Portfolio optimization using SciPy
7. Factor strategy construction
8. Factor strategy backtesting
9. Strategy performance evaluation
10. Portfolio optimization
11. Constrained portfolio robustness
12. Walk-forward portfolio backtesting
13. Final analysis and investment report

## Methods and Tools

**Languages:** Python

**Libraries:** NumPy, pandas, Matplotlib, SciPy, scikit-learn, yfinance

**Methods explored:**
- Return and risk measurement
- Portfolio diversification
- Mean-variance optimization
- Momentum and low-volatility strategies
- Long-only portfolio constraints
- Covariance estimation and sensitivity analysis
- Rolling walk-forward backtesting
- Transaction-cost sensitivity analysis

## Key Research Questions

- How do factor-based strategies compare with equal-weight portfolios?
- Does portfolio optimization improve out-of-sample performance?
- How sensitive are optimized allocations to estimation assumptions?
- How do rolling strategies perform after modeled transaction costs?

## Limitations

The universe contains only five stocks, and the findings depend on the selected sample period, strategy definitions, and transaction-cost assumptions. Historical backtests do not guarantee future performance.

## Disclaimer

This project is for educational and research purposes only. It is not investment advice.
