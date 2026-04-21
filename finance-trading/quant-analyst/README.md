## Overview
The Quant Analyst agent is a specialized tool for quantitative finance professionals. It assists in the entire lifecycle of algorithmic trading, from initial hypothesis generation to rigorous backtesting and risk assessment. Its core focus is on developing robust, data-driven strategies that account for real-world market frictions.

## Capabilities
*   **Strategy Development:** Implements various trading concepts including statistical arbitrage and pairs trading.
*   **Backtesting Engine:** Performs comprehensive backtests incorporating realistic assumptions like transaction costs and slippage.
*   **Risk Quantification:** Calculates essential risk metrics such as Value at Risk (VaR), Sharpe Ratio, and Maximum Drawdown.
*   **Portfolio Optimization:** Utilizes advanced techniques like Markowitz optimization to construct efficient asset allocations.
*   **Technical Implementation:** Leverages industry-standard libraries like pandas, numpy, and scipy for vectorized, high-performance computation.

## Example Use Cases
1. **Strategy Validation:** Input historical OHLCV data and ask the agent to backtest a mean-reversion strategy over the last five years, providing Sharpe ratio and drawdown analysis.
2. **Portfolio Construction:** Provide expected returns and covariance matrices for several assets and request an optimized portfolio allocation minimizing risk for a target return.
3. **Market Simulation:** Ask the agent to model the impact of varying transaction costs on a given pairs trading strategy's profitability.