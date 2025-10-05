Multi-Asset Portfolio Optimization and Risk Analysis Project
This project is a comprehensive Jupyter Notebook that demonstrates how to optimize a multi-asset portfolio and analyze its risk using financial modeling techniques such as Modern Portfolio Theory (MPT) and Monte Carlo simulation.

Project Introduction
The project aims to guide investors on how to create and manage their portfolios and evaluate risk. It uses a "universe of assets" consisting of 15 popular ETFs and stocks from major US companies across various sectors.

The workflow is divided into six main stages, each serving a specific purpose:

Data Collection and Preparation: Required financial data (stock closing prices) are downloaded from Yahoo Finance and prepared for analysis.

Exploratory Data Analysis (EDA): Annual returns, volatility, and correlation analyses are performed to understand the historical performance of assets and their interrelationships.

Portfolio Optimization and Efficient Frontier: Modern Portfolio Theory is applied to find optimal portfolio weights for the Maximum Sharpe Ratio and Minimum Variance portfolios. The "Efficient Frontier" is then plotted.

Risk Management and Stress Testing: Value at Risk (VaR) and Conditional Value at Risk (CVaR) are calculated to measure the risk of the optimal portfolio. Stress tests are conducted against historical events like the 2008 Financial Crisis and the COVID-19 Pandemic Crash.

Dynamic Backtesting: The optimized portfolio strategy is backtested against historical data to evaluate its performance over time. The portfolio is re-optimized every 3 months, and its results are compared to a benchmark like the SPY ETF.

Future Projections: Monte Carlo simulation is used to forecast the portfolio's potential future performance over a specified period.

Libraries Used
The technical foundation of this project relies on powerful Python libraries for financial data analysis and scientific computing:

yfinance: Used to download financial data from Yahoo Finance via an API.

pandas: Used to store and manipulate portfolio data in a DataFrame structure.

numpy: Essential for numerical operations and mathematical calculations, especially for returns and covariance matrix computations.

scipy.optimize: Provides the minimize function to solve constrained optimization problems for portfolio optimization.

quantstats: Used to analyze backtesting results and generate a comprehensive performance report. This library automatically calculates many financial metrics such as Sharpe Ratio, Sortino Ratio, and Maximum Drawdown.

matplotlib and seaborn: Used to visualize optimization results and simulation outputs.

Project Stages and Technical Details
Stage 1: Data Fetching and Pre-processing
The project analyzes a portfolio of 15 different assets (various ETFs and S&P 500 stocks). Daily closing prices from 2006-01-01 to 2023-12-31 are downloaded using the yfinance.download() function. Missing data (NaN) are cleaned using the dropna() method, and daily returns are calculated using the pct_change() function.

Stage 2: Exploratory Data Analysis
This stage examines the fundamental statistical characteristics of the assets:

Annualized Performance: The mean and standard deviation of daily returns are annualized, assuming 252 trading days per year.

Annualized Return = returns.mean() * 252

Annualized Volatility = returns.std() * np.sqrt(252)

Correlation Matrix: returns.corr() calculates the correlations between assets. A heatmap is plotted to visualize these relationships, which helps in understanding the potential for portfolio diversification.

Rolling Correlation: The rolling() method is used to dynamically analyze how the correlation between assets (e.g., SPY and AAPL) changes over time, showing how asset relationships can shift with market conditions.

Stage 3: Portfolio Optimization with Modern Portfolio Theory
This is the core of the project, solving two primary optimization problems:

Portfolio Performance Function: The portfolio_performance function calculates the annualized return and volatility for a given set of weights, mean returns, and a covariance matrix.

Portfolio Return=∑ 
i=1
n
​
 w 
i
​
 ×μ 
i
​
 ×252

Portfolio Volatility= 
w 
T
 ⋅Σ⋅w

​
 × 
252

​
 

Maximum Sharpe Ratio: The scipy.optimize.minimize function is used to find the portfolio weights that yield the highest Sharpe Ratio. The objective function is to minimize the negative Sharpe Ratio (risk-free rate is assumed to be 1%).

Minimum Variance: The minimize function is also used to find the weights that result in the lowest portfolio volatility, by directly minimizing the portfolio's standard deviation.

Efficient Frontier: 25,000 random portfolios are generated (using a Monte Carlo simulation) to visualize the possible risk-return combinations. The graph plots these random portfolios along with the highlighted optimal portfolios.

Stage 4: Advanced Risk Analysis
To gain a deeper understanding of the risks associated with the Maximum Sharpe Ratio Portfolio, the following analyses are performed on its returns series:

Value at Risk (VaR): VaR estimates the potential maximum loss of a portfolio over a specific time horizon (daily in this project) within a given confidence interval (95%). For example, a VaR of -1.54% means there is a 5% chance the portfolio will lose more than 1.54% in a single day.

Historical VaR: This method uses the historical returns to directly find the 5th percentile (.quantile(0.05)) of the distribution.

Parametric VaR: This method assumes that portfolio returns follow a normal distribution. It is calculated using the portfolio's mean (μ) and standard deviation (σ) along with the z-score corresponding to the confidence level (VaR=μ+σ×z).

Conditional Value at Risk (CVaR): CVaR is a more advanced risk measure than VaR. It calculates the expected average loss, given that the loss exceeds the VaR threshold. It provides a more comprehensive view of the portfolio's "tail risk."

Historical Stress Tests: These tests evaluate the portfolio's resilience against significant past market shocks:

2008 Financial Crisis (Sep 2008 - Mar 2009): The cumulative loss of the portfolio during this period is calculated.

COVID-19 Pandemic Crash (Feb-Mar 2020): The cumulative loss during this crash is also calculated.

Stage 5: Dynamic Portfolio Backtesting
Instead of using a static portfolio, this stage simulates a more realistic dynamic management strategy.

Dynamic Optimization: The portfolio is re-optimized every 3 months (rebalance_frequency), using a 3-year "lookback window" (lookback_window) of past data. This simulates a strategy that adapts to changing market conditions. In each re-optimization step, new "Maximum Sharpe Ratio" weights are determined for the upcoming 3-month period.

Return Calculation: For each 3-month period, the returns are calculated using the new weights. The resulting daily return series are then concatenated to form a complete backtesting performance history.

Comprehensive Report: The quantstats.reports.html() function is used to generate a detailed HTML report (dynamic_strategy_report_en.html) of the backtesting performance. This report includes:

Cumulative Returns: The total return of the strategy over the backtesting period.

Annualized Returns and Volatility: Average yearly performance metrics.

Max Drawdown: The largest peak-to-trough decline during the backtesting period.

Sharpe and Sortino Ratios: Risk-adjusted return metrics.

Benchmark Comparison: The portfolio's performance is analyzed against a benchmark index like the SPY ETF.

Stage 6: Monte Carlo Simulation for Future Projections
Finally, a Monte Carlo simulation is performed to project the portfolio's potential future performance.

Starting Value: The simulation begins with an initial portfolio value of $100,000.

Covariance Matrix: The simulation uses the full dataset's mean and covariance matrix. The Cholesky decomposition (numpy.linalg.cholesky) of the covariance matrix is used to generate correlated random variables, which ensures that the simulated asset returns maintain their historical relationships.

Simulation: The simulation runs 1000 times to generate 10-year (2520 trading days) performance paths for the portfolio.

Analysis and Visualization: The distribution of the final portfolio values is plotted using a histogram. Key statistical percentiles (5th, 50th/median, and 95th) are calculated to provide a probabilistic range of potential outcomes. This helps an investor understand the risk and potential reward of the strategy over the long term.
