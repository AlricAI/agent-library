## Overview
This agent functions as a specialized Quantitative Analyst, designed to build, test, and validate sophisticated financial models for algorithmic trading. It moves beyond simple return calculations by focusing heavily on risk-adjusted performance, robust backtesting methodologies, and advanced statistical techniques.

## Capabilities
*   **Strategy Development:** Builds quantitative trading strategies from scratch using vectorized operations in pandas, numpy, and scipy.
*   **Risk Analysis:** Implements critical risk metrics such as Value at Risk (VaR), Sharpe Ratio, and Maximum Drawdown analysis.
*   **Portfolio Optimization:** Creates models based on established frameworks like Markowitz and Black-Litterman for optimal asset allocation.
*   **Time Series Forecasting:** Develops time series models to predict market movements and identify arbitrage opportunities.
*   **Derivatives Pricing:** Calculates options pricing, including the Greeks (Delta, Gamma, Theta, Vega) for complex derivatives strategies.
*   **Robust Testing:** Emphasizes out-of-sample testing, incorporating realistic assumptions like transaction costs and slippage to prevent overfitting.

## Example Use Cases
1. **Strategy Backtesting:** Input historical OHLCV data and request a backtest of a pairs trading strategy, receiving detailed performance metrics including Sharpe Ratio and maximum drawdown.
2. **Portfolio Construction:** Provide expected returns and covariance matrices for a basket of assets and ask the agent to optimize the portfolio weights using the Black-Litterman model.
3. **Risk Assessment:** Submit a proposed trading book and request a comprehensive risk report, including calculated VaR at a specified confidence level (e.g., 99%).
4. **Derivatives Modeling:** Upload current market prices for an underlying asset and options chain, and ask the agent to calculate the theoretical price of a complex spread and its associated Greeks.