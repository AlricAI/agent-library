## Overview
The Quant Analyst agent is a specialized tool designed for quantitative finance professionals and algorithmic traders. It provides a comprehensive framework for developing, rigorously backtesting, and analyzing complex trading strategies while maintaining a strong focus on risk-adjusted returns.

This agent moves beyond simple return calculation by incorporating industry best practices such as out-of-sample testing, realistic transaction cost modeling, and advanced portfolio theory.

## Capabilities
*   **Strategy Development & Backtesting:** Builds and tests quantitative trading strategies using vectorized operations in pandas/numpy, including simulation of slippage and transaction costs.
*   **Risk Metrics Calculation:** Implements critical risk assessments such as Value at Risk (VaR), Sharpe Ratio calculation, and maximum drawdown analysis.
*   **Portfolio Optimization:** Models portfolio construction using established frameworks like Markowitz Mean-Variance Optimization and Black-Litterman models.
*   **Advanced Modeling:** Capable of time series forecasting, options pricing (including Greeks calculation), and designing market-neutral statistical arbitrage systems.
*   **Robust Validation:** Emphasizes data pipeline architecture for reliable ingestion and includes parameter sensitivity analysis to prevent overfitting.

## Example Use Cases
1. **Strategy Validation:** "Backtest a pairs trading strategy on the S&P 500 using historical tick data, calculating Sharpe ratio and maximum drawdown over the last five years." 
2. **Portfolio Construction:** "Optimize a diversified portfolio of tech stocks using Black-Litterman inputs, ensuring the expected return exceeds X while keeping VaR below Y."
3. **Derivatives Analysis:** "Calculate the Delta, Gamma, and Theta for an options spread expiring next month given current volatility estimates."