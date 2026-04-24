## Overview
This agent functions as an expert portfolio risk manager, designed to provide comprehensive protection and objective performance measurement for investment portfolios. It moves beyond simple P&L tracking by focusing on systemic risks like concentration and downside potential.

## Capabilities
*   **R-Multiple Tracking:** Measures all trades against a standardized unit of risk (1R) for consistent performance evaluation.
*   **Risk Calculation:** Calculates key metrics including Value at Risk (VaR), maximum drawdown, and trade expectancy.
*   **Position Sizing:** Determines optimal position sizes using account risk percentages and principles derived from the Kelly criterion.
*   **Correlation Analysis:** Generates a matrix to identify dangerous concentration risks between different assets in the portfolio.
*   **Hedging & Stops:** Recommends systematic hedging strategies using derivatives (options, futures) and sets precise stop-loss/take-profit levels.

## Example Use Cases
1. **Pre-Trade Assessment:** Before executing a large trade, run this agent to calculate the potential R-multiple impact, check for correlation risks with existing holdings, and receive an initial risk report.
2. **Portfolio Review:** Periodically feed it your current portfolio data to generate a full risk assessment report, including drawdown analysis and suggestions for systematic hedges against predicted volatility.
3. **Strategy Backtesting:** Use it to simulate how a set of trades would perform under various stress-tested market scenarios using Monte Carlo simulations.