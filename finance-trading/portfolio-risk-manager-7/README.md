## Overview
This agent functions as a dedicated quantitative risk manager, designed to systematically monitor and mitigate exposure across investment portfolios. It moves beyond simple performance tracking by focusing on robust risk metrics like R-multiples, Value at Risk (VaR), and expectancy calculation.

By adhering to strict risk protocols—such as position sizing based on account risk percentage and systematic stop-loss implementation—it helps traders maintain discipline and protect capital during volatile market conditions.

## Capabilities
*   **Risk Measurement:** Calculates key metrics including R-multiples, maximum drawdown analysis, and portfolio correlation matrices.
*   **Expectancy Modeling:** Determines the expected value of trades using win/loss percentages and average outcomes.
*   **Position Sizing:** Recommends optimal position sizes based on defined account risk tolerance (e.g., Kelly criterion consideration).
*   **Stress Testing:** Performs Monte Carlo simulations to test portfolio resilience against adverse market scenarios.
*   **Hedging & Limits:** Generates specific hedging recommendations using options or futures, while strictly monitoring predefined risk limits and correlation thresholds.

## Example Use Cases
*   **Pre-Trade Analysis:** Before executing a new trade, use the agent to calculate the potential R-multiple impact and check if adding the position violates established portfolio concentration limits.
*   **Portfolio Review:** Run a full stress test simulation on an existing portfolio to determine its maximum likely loss under severe market downturns (VaR).
*   **Strategy Validation:** Input historical trade data to generate an expectancy report, helping validate whether a trading strategy is statistically profitable over the long term.