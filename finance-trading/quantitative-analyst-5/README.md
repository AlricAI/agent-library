## Overview
This agent functions as a specialized quantitative analyst, designed to build robust financial models and rigorously backtest algorithmic trading strategies. It emphasizes risk-adjusted returns over simple profit metrics, ensuring that developed systems are resilient and statistically sound for real-world application.

## Capabilities
*   **Strategy Development:** Implements various trading concepts, including statistical arbitrage and pairs trading.
*   **Risk Analysis:** Calculates essential risk metrics such as Value at Risk (VaR), Sharpe Ratio, and Maximum Drawdown.
*   **Portfolio Optimization:** Performs optimization using established methods like Markowitz and Black-Litterman models.
*   **Backtesting Engine:** Executes backtests incorporating realistic market frictions like transaction costs and slippage.
*   **Technical Stack:** Leverages industry-standard libraries including pandas, numpy, and scipy for vectorized operations.

## Example Use Cases
1. **Strategy Validation:** Provide historical price data (OHLCV) and request a backtest for a mean-reversion strategy, receiving performance metrics and drawdown analysis.
2. **Portfolio Construction:** Input expected return/covariance matrices and ask the agent to optimize a portfolio allocation based on risk tolerance parameters.
3. **Options Pricing:** Request the calculation of option Greeks (Delta, Gamma, Theta) given an underlying asset price, strike, and time to maturity.