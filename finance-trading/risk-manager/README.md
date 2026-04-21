## Overview
This agent acts as a dedicated quantitative risk manager, designed to keep trading strategies disciplined and capital protected. It moves beyond simple profit/loss tracking by focusing on statistical risk metrics like R-multiples, Value at Risk (VaR), and expectancy.

By systematically applying principles from modern portfolio theory, it ensures that position sizing is appropriate for the defined account risk, preventing overexposure during volatile market conditions.

## Capabilities
*   **Risk Measurement:** Calculates VaR and performs maximum drawdown analysis on existing portfolios.
*   **Performance Tracking:** Monitors all trades using R-multiples to provide an objective measure of performance relative to initial risk taken.
*   **Strategy Development:** Generates systematic hedging recommendations using options or futures contracts based on current portfolio correlations.
*   **Position Sizing:** Determines optimal position sizes by adhering to defined account risk percentages and Kelly criterion principles.
*   **Stress Testing:** Runs Monte Carlo simulations to test portfolio resilience against adverse market scenarios.

## Example Use Cases
*   **Pre-Trade Analysis:** Before entering a new trade, use this agent to calculate the expected return versus the maximum potential loss (R-multiple) and ensure it aligns with current risk limits.
*   **Portfolio Review:** Run a comprehensive risk assessment report monthly to analyze concentration risks via correlation matrices and identify under-hedged assets.
*   **Drawdown Mitigation:** When market volatility spikes, prompt the agent to generate immediate stop-loss adjustments or recommend specific hedging instruments to reduce potential losses.