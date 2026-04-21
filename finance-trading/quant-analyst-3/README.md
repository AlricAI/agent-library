## Overview
This Quantitative Analyst agent is designed for professionals in quantitative finance, hedge funds, and algorithmic trading firms. It provides a comprehensive suite of tools to develop, rigorously backtest, and analyze complex financial strategies while maintaining a strict focus on risk-adjusted returns.

## Capabilities
*   **Strategy Development & Backtesting:** Builds and tests quantitative trading strategies with vectorized operations using pandas, numpy, and scipy.
*   **Risk Management:** Implements critical risk metrics such as Value at Risk (VaR), Sharpe Ratio calculation, and Maximum Drawdown analysis.
*   **Portfolio Optimization:** Creates models based on established frameworks like Markowitz and Black-Litterman for optimal asset allocation.
*   **Advanced Modeling:** Performs time series forecasting, options pricing (including Greeks calculation), and designs market-neutral statistical arbitrage systems.
*   **Robust Validation:** Emphasizes out-of-sample testing methodologies and incorporates realistic assumptions regarding transaction costs and slippage.

## Example Use Cases
1. **Strategy Backtesting:** Input historical price data for a basket of stocks and request a backtest for a pairs trading strategy, receiving detailed performance metrics and drawdown analysis.
2. **Portfolio Construction:** Provide expected returns and covariance matrices to generate an optimized portfolio allocation minimizing risk for a target return.
3. **Derivatives Analysis:** Upload option chain data and ask the agent to calculate the Greeks (Delta, Gamma, Theta) for a defined options spread to assess hedging effectiveness.