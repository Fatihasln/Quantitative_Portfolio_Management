# Multi-Asset Portfolio Optimization and Risk Analysis

A comprehensive Python framework for constructing, optimizing, and analyzing a multi-asset financial portfolio using Modern Portfolio Theory (MPT) and advanced risk management techniques.

## 📖 Project Overview

This project implements a complete pipeline for quantitative portfolio management:
1.  **Data Acquisition:** Fetches historical price data for ETFs and stocks.
2.  **Exploratory Analysis:** Calculates performance metrics and analyzes asset correlations.
3.  **Portfolio Optimization:** Uses Monte Carlo simulation and optimization techniques to find the Efficient Frontier, Minimum Variance Portfolio, and Maximum Sharpe Ratio Portfolio.
4.  **Risk Management:** Calculates Value at Risk (VaR), Conditional VaR, and performs stress tests against historical market crashes.
5.  **Dynamic Backtesting:** Implements and backtests a dynamic quarterly rebalancing strategy.
6.  **Future Projection:** Runs Monte Carlo simulations to project potential future portfolio values.

## 🛠️ Installation & Dependencies

1.  **Clone the repository:**
    ```bash
    git clone <[your-repo-url](https://github.com/Fatihasln/Quantitative_Portfolio_Management
)>
    cd Multi_Asset_Portfolio_Optimization_and_Risk_Analysis
    ```

2.  **Install required libraries:**
    ```bash
    pip install yfinance pandas numpy matplotlib seaborn scipy quantstats
    ```

## 📈 Usage

1.  **Run the Jupyter Notebook:**
    Open and run all cells in the `Multi_Asset_Portfolio_Optimization_and_Risk_Analysis.ipynb` notebook.

2.  **Configure the Asset Universe (Optional):**
    Modify the `tickers` list in the first code cell to analyze your own set of assets.
    ```python
    tickers = ['SPY', 'QQQ', 'TLT', 'GLD', 'IYR', 'AAPL', 'MSFT', ...]
    ```

3.  **Adjust Parameters (Optional):**
    Change the `start_date`, `end_date`, `rebalance_frequency`, `lookback_window`, or Monte Carlo `num_simulations` and `num_years` to suit your analysis.

## 📁 Project Structure

*   `Multi_Asset_Portfolio_Optimization_and_Risk_Analysis.ipynb`: The main Jupyter notebook containing the complete code and analysis.
*   `dynamic_strategy_report_en.html`: (Generated) Detailed performance report of the dynamic strategy compared to the benchmark (SPY).

## 🧠 Key Features

*   **Data Handling:** Automated data download and cleaning from Yahoo Finance.
*   **Visualization:** Correlation heatmaps, rolling correlations, and Efficient Frontier plots.
*   **Optimization:** Identification of optimal portfolios (Min Variance, Max Sharpe) using `scipy.optimize`.
*   **Risk Metrics:** Calculation of Historical/Parametric VaR, CVaR, and stress testing.
*   **Backtesting:** Implementation of a dynamic, quarterly rebalancing strategy.
*   **Performance Reporting:** Automatic generation of a professional-grade performance report using `quantstats`.
*   **Future Simulation:** Monte Carlo simulation to project future portfolio value distributions.

## 📊 Sample Outputs

The notebook generates numerous charts and outputs, including:
*   Asset Correlation Matrix Heatmap
*   1-Year Rolling Correlation (SPY vs. AAPL)
*   Efficient Frontier with Optimal Portfolios
*   Histogram of Simulated Future Portfolio Values
*   A detailed HTML performance report with metrics like:
    *   Cumulative Returns
    *   Annualized Returns & Volatility
    *   Sharpe Ratio
    *   Maximum Drawdown
    *   Alpha/Beta vs. Benchmark
    *   Worst Drawdown Periods

## ⚠️ Important Disclaimer

**This project is for educational and research purposes only.** It is not financial advice. Past performance is not indicative of future results. Investing in financial markets involves risk, including the possible loss of principal. Always conduct your own research and consider seeking advice from a qualified professional before making any investment decisions.

## 👨‍💻 Author

Mehmet Fatih CIFTASLAN

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

*   Built with the help of the `yfinance`, `pandas`, and `quantstats` libraries.
*   Inspired by the principles of Modern Portfolio Theory (Harry Markowitz).
