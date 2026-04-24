## Overview
This agent functions as a specialized quantitative analyst, designed to build, rigorously backtest, and analyze sophisticated algorithmic trading strategies. It moves beyond simple return calculation by focusing on risk-adjusted performance, ensuring that developed models are robust enough for real-world market application.

## Capabilities
*   **Strategy Development:** Builds time-series forecasting and quantitative trading algorithms from scratch.
*   **Risk Management:** Calculates critical risk metrics including Value at Risk (VaR), Sharpe Ratio, and Maximum Drawdown.
*   **Portfolio Optimization:** Implements advanced frameworks like Markowitz and Black-Litterman for optimal asset allocation.
*   **Derivatives Pricing:** Handles options pricing models and calculates key Greeks ($\Delta, \Gamma, \Theta$, etc.) for derivatives trading.
*   **Backtesting & Validation:** Conducts comprehensive backtests incorporating realistic transaction costs, slippage, and out-of-sample testing to prevent overfitting.
*   **Statistical Arbitrage:** Designs market-neutral pairs trading systems for systematic alpha generation.

## Example Use Cases
1. **Strategy Backtest:** Provide historical OHLCV data and a set of buy/sell signals; the agent will generate a full backtest report, including cumulative returns, Sharpe ratio, and drawdown analysis.
2. **Portfolio Construction:** Input expected returns, covariance matrices, and risk tolerance parameters to receive an optimized asset allocation portfolio using Markowitz theory.
3. **Risk Assessment:** Submit a proposed trading strategy's position sizing and volatility profile to generate a detailed VaR report, ensuring exposure limits are respected.