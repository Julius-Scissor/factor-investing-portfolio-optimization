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

## Project Notebooks

The project is organized into 13 notebooks, progressing from data preparation to factor research and portfolio optimization.

| # | Notebook | Topics |
|---:|---|---|
| 1 | [Data Collection and Preprocessing](notebooks/01_Data_Collection_and_Preprocessing.ipynb) | Market data, cleaning, adjusted prices |
| 2 | [Stock Performance and Risk Analysis](notebooks/02_Stock_Performance_and_Risk_Analysis.ipynb) | Returns, volatility, risk metrics |
| 3 | [Portfolio Construction and Diversification](notebooks/03_Portfolio_Construction_and_Diversification.ipynb) | Portfolio weights, diversification |
| 4 | [Modern Portfolio Theory](notebooks/04_Modern_Portfolio_Theory.ipynb) | Risk-return trade-offs |
| 5 | [Efficient Frontier and Monte Carlo Optimization](notebooks/05_Efficient_Frontier_and_Monte_Carlo_Optimization.ipynb) | Random portfolios, efficient frontier |
| 6 | [Portfolio Optimization Using SciPy](notebooks/06_Portfolio_Optimization_Using_SciPy.ipynb) | Numerical optimization |
| 7 | [Factor Strategy Construction](notebooks/07_Factor_Strategy_Construction.ipynb) | Factor signals and portfolio formation |
| 8 | [Factor Strategy Backtesting](notebooks/08_Factor_Strategy_Backtesting.ipynb) | Strategy returns and transaction costs |
| 9 | [Strategy Performance Evaluation](notebooks/09_Strategy_Performance_Evaluation.ipynb) | Risk-adjusted performance comparison |
| 10 | [Portfolio Optimization](notebooks/10_Portfolio_Optimization.ipynb) | Minimum variance, maximum Sharpe |
| 11 | [Constrained Portfolio Robustness](notebooks/11_Constrained_Portfolio_Robustness.ipynb) | Weight caps, estimation sensitivity |
| 12 | [Walk-Forward Portfolio Backtesting](notebooks/12_Walk_Forward_Portfolio_Backtesting.ipynb) | Rolling training and out-of-sample evaluation |
| 13 | [Final Project Analysis and Investment Report](notebooks/13_Final_Project_Analysis_and_Investment_Report.ipynb) | Consolidated findings and limitations |

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

## Research Reports

The project documentation is available in Markdown and PDF formats.

- [**Standard Research Report (PDF)**](reports/Factor_Investing_Portfolio_Optimization_Report.pdf)
- [**IEEE-Style Research Paper (PDF)**](reports/Factor_Investing_Portfolio_Optimization_IEEE_Report.pdf)
- [**Editable Report (Markdown)**](reports/project_report.md)

The reports document the research methodology, factor-strategy evaluation, portfolio optimization experiments, walk-forward backtesting, results, and limitations.

## Disclaimer

This project is for educational and research purposes only. It is not investment advice.
