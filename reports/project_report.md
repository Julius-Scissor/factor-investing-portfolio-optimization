# Factor Investing and Portfolio Optimization in Indian Equities

## Table of Contents

1. [Introduction](#1-introduction)
2. [Research Objectives](#2-research-objectives)
3. [Research Questions](#3-research-questions)
4. [Data and Methodology](#4-data-and-methodology)
5. [Results and Discussion](#5-results-and-discussion)
6. [Limitations](#6-limitations)
7. [Conclusion](#7-conclusion)
8. [Future Work](#8-future-work)
9. [Reproducibility](#9-reproducibility)
10. [Disclaimer](#10-disclaimer)
11. [References](#11-references)
12. [Technical Notes](#12-technical-notes)

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

$$
r_t = \frac{P_t}{P_{t-1}} - 1
$$

For a portfolio with asset weights \(w_i\) and asset returns \(r_{i,t}\), the portfolio return is

$$
r_{p,t} = \sum_{i=1}^{N} w_i r_{i,t}
$$

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

## 5. Results and Discussion

### 5.1 Factor Strategy Performance

The factor-strategy experiment compares equal-weight, momentum, and low-volatility portfolios with the NIFTY 50 reference over the evaluation period reported in Notebook 9.

| Strategy | Cumulative Return | CAGR | Annualized Volatility | Sharpe Ratio | Maximum Drawdown |
|---|---:|---:|---:|---:|---:|
| Equal-weight | 75.29% | 12.33% | 15.33% | 0.836 | -15.96% |
| Momentum | 69.17% | 11.51% | 17.16% | 0.721 | -22.25% |
| Low-volatility | 113.90% | 17.07% | 17.62% | 0.983 | -25.38% |
| NIFTY 50 | 91.64% | 14.43% | 13.94% | 1.037 | -17.23% |

The evaluation covers February 1, 2021, through December 31, 2025, with 1,216 daily observations.

The low-volatility strategy achieved the highest CAGR among the three tested portfolio strategies, at 17.07%, and recorded a Sharpe ratio of 0.983. The NIFTY 50 benchmark recorded the highest Sharpe ratio in this comparison, at 1.037, alongside lower annualized volatility than the three strategies.

These results illustrate that a higher annualized return does not necessarily imply the highest risk-adjusted performance. The findings are specific to the selected stocks, signal definitions, and evaluation period.

### 5.2 Fixed-Weight Portfolio Optimization

| Portfolio | Cumulative Return | Annualized Return | Annualized Volatility | Sharpe Ratio | Maximum Drawdown |
|---|---:|---:|---:|---:|---:|
| Equal-weight | 17.35% | 8.49% | 13.92% | 0.224 | -15.22% |
| Minimum variance | 7.09% | 3.55% | 14.45% | -0.102 | -17.27% |
| Maximum Sharpe | 18.60% | 9.07% | 17.28% | 0.241 | -21.73% |
| NIFTY 50 | 20.24% | 9.84% | 12.97% | 0.326 | -15.77% |

The evaluation used a chronological training and test split, with the held-out test period spanning January 1, 2024, through December 31, 2025. The test set contained 495 daily return observations.

The NIFTY 50 benchmark outperformed all three portfolio allocations on cumulative return, annualized return, and Sharpe ratio. Among the portfolio allocations, the maximum-Sharpe portfolio achieved the highest cumulative and annualized returns, while the minimum-variance portfolio had the lowest annualized volatility.

The minimum-variance portfolio nevertheless recorded a negative Sharpe ratio in the test period. This illustrates that minimizing estimated portfolio variance does not guarantee superior realized performance. These findings are specific to the selected assets, training window, optimization constraints, and evaluation period.

### 5.3 Sensitivity to Optimization Assumptions

The robustness experiment examined the effects of position limits, covariance estimation, and expected-return estimation windows.

The saved outputs showed that optimized allocations changed materially when the covariance estimator or expected-return window changed. In particular, the maximum-Sharpe allocation to TCS and Infosys shifted substantially across the compared expected-return estimation windows.

This sensitivity highlights a key limitation of mean-variance optimization: estimated expected returns and covariance matrices contain uncertainty. An optimizer can respond strongly to small changes in estimated inputs, producing allocations that may not remain stable out of sample.

### 5.4 Walk-Forward Backtesting

The walk-forward experiment repeatedly estimated portfolio weights using historical observations and evaluated subsequent returns. The saved results included a rolling minimum-variance portfolio, a rolling maximum-Sharpe portfolio, and an equal-weight reference portfolio.

| Strategy | Cumulative Return | Annualized Return | Sharpe Ratio | Maximum Drawdown |
|---|---:|---:|---:|---:|
| Equal-weight | 32.10% | 10.10% | 0.336 | -15.22% |
| Rolling minimum variance | 29.30% | 9.29% | 0.283 | -13.29% |
| Rolling maximum Sharpe | 27.63% | 8.80% | 0.229 | -18.56% |

The walk-forward experiment evaluated 12 scheduled rebalances. Equal-weight achieved the highest cumulative return, annualized return, and Sharpe ratio among the three portfolios. The rolling minimum-variance portfolio had the least severe maximum drawdown, at -13.29%.

The rolling maximum-Sharpe strategy did not outperform equal-weight in this experiment. These findings are specific to the selected stock universe, estimation windows, rebalancing schedule, and backtesting assumptions.

### 5.5 Overall Interpretation

Across the experiments, no single approach dominated every comparison. Low-volatility performed strongly in the factor-strategy experiment, the NIFTY 50 reference performed strongly in the fixed-weight held-out test, and equal-weight remained competitive in the walk-forward evaluation.

These findings should not be interpreted as a direct ranking across all strategies because the experiments use different evaluation windows and portfolio-construction procedures. A fair unified comparison would require aligned dates, consistent benchmark returns, and common transaction-cost assumptions.

The broader lesson is that portfolio optimization is not guaranteed to improve realized out-of-sample performance. Simple allocation rules can remain competitive, while optimization-based allocations may be sensitive to estimation choices.

## 6. Limitations

Several limitations should be considered when interpreting the results.

### 6.1 Limited Stock Universe

The study considers only five Indian equities. Although these companies operate across multiple sectors, the universe is too narrow to represent the broader Indian equity market. Results may differ substantially for a larger universe that includes additional sectors and market-capitalization groups.

### 6.2 Estimation Uncertainty

Portfolio optimization depends on estimated expected returns and covariance matrices. These estimates are uncertain and may change with the sample period or estimation method. The observed sensitivity of portfolio weights indicates that optimized allocations should not be treated as uniquely reliable solutions.

### 6.3 Historical Backtesting

Backtests evaluate strategies using historical observations. Market conditions, correlations, volatility, and return patterns can change over time. Historical performance therefore does not establish that a strategy will perform similarly in the future.

### 6.4 Trading-Cost Assumptions

Transaction costs are modeled in the relevant experiments. Actual trading may involve additional costs, including taxes, bid-ask spreads, slippage, and market impact. Realized performance could consequently differ from simulated performance.

### 6.5 Differences Between Experiments

The notebooks use different evaluation windows and portfolio-construction procedures. Their performance figures should not be combined into a single ranking without aligning evaluation dates, benchmark returns, rebalancing assumptions, and transaction-cost conventions.

## 7. Conclusion

This project develops an end-to-end quantitative portfolio research workflow, covering historical market-data preparation, stock-level risk analysis, factor-strategy construction, mean-variance optimization, constrained allocation, robustness analysis, and walk-forward backtesting.

The experiments demonstrate that the relative performance of portfolio strategies depends on the evaluation period and modeling assumptions. The low-volatility strategy performed strongly in the factor-strategy comparison, the NIFTY 50 reference performed strongly in the fixed-weight held-out experiment, and equal-weight remained competitive in walk-forward testing.

The robustness analysis also showed that optimized portfolio weights can change substantially when estimation assumptions change. This highlights the importance of out-of-sample evaluation, realistic trading-cost assumptions, and careful interpretation of optimized allocations.

The central conclusion is that mathematical optimization alone does not guarantee superior realized performance. A credible quantitative investment process must evaluate not only theoretical portfolio properties but also the stability and performance of strategies on unseen data.

## 8. Future Work

Several extensions could improve the scope and robustness of this research:

1. Expand the stock universe to include more companies and sectors.
2. Evaluate additional factor signals and alternative signal lookback windows.
3. Test multiple chronological out-of-sample periods and market regimes.
4. Incorporate more realistic transaction costs and turnover constraints.
5. Compare alternative covariance estimators and robust optimization methods.
6. Evaluate performance across different rebalance frequencies.

## 9. Reproducibility

The analysis is organized into numbered Jupyter notebooks, covering data collection, exploratory analysis, portfolio construction, factor strategies, optimization, robustness testing, and final evaluation.

For reproducibility, notebooks should be executed in numerical order in a clean runtime where practical. The Python dependencies are listed in `requirements.txt`.

## 10. Disclaimer

This project is an academic exercise in quantitative finance and portfolio research. The results are based on historical data and simulated strategies and should not be interpreted as investment advice or a guarantee of future performance.

## 11. References

1. Markowitz, H. (1952). Portfolio Selection. *The Journal of Finance, 7*(1), 77–91. https://doi.org/10.1111/j.1540-6261.1952.tb01525.x

2. Sharpe, W. F. (1966). Mutual Fund Performance. *The Journal of Business, 39*(1), 119–138. https://doi.org/10.1086/294846

3. Yahoo Finance. Historical market data. https://finance.yahoo.com/

4. yfinance documentation. https://ranaroussi.github.io/yfinance/

5. NumPy documentation. https://numpy.org/doc/

6. pandas documentation. https://pandas.pydata.org/docs/

7. SciPy documentation. https://docs.scipy.org/doc/scipy/

8. scikit-learn documentation. https://scikit-learn.org/stable/

## 12. Technical Notes

### Software and Libraries

The project is implemented in Python using Jupyter notebooks. The principal libraries include:

- **NumPy:** numerical computations and array operations.
- **pandas:** time-series data handling and data analysis.
- **Matplotlib:** charts and visualizations.
- **SciPy:** numerical optimization.
- **scikit-learn:** statistical and machine-learning utilities where applicable.
- **yfinance:** retrieval of historical market data.
- **Jupyter:** interactive notebook execution and documentation.

### Reproducibility Considerations

For reproducibility, notebooks should be executed in numerical order in a clean runtime where practical. The Python dependencies are listed in `requirements.txt`.

The exact Python and library versions used for the reported results should be recorded when the final experiments are rerun. The historical data retrieval date should also be documented because the data provider may revise its records.

### Performance Metric Conventions

Performance metrics should be interpreted according to the calculation conventions implemented in the corresponding notebook. Annualization factors, risk-free-rate assumptions, return frequencies, missing-data treatment, and transaction-cost calculations can affect reported values.

When comparing strategies, the same evaluation dates and benchmark-return conventions should be used. Results from separate experiments should remain clearly distinguished when their evaluation periods or implementation assumptions differ.
