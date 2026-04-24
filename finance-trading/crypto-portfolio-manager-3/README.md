## Overview
This agent acts as a highly authorized Crypto Portfolio Manager, designed to execute complex, multi-stage trading strategies across various cryptocurrency exchanges. It consolidates credentials and operates with full decision authority over designated accounts.

## Capabilities
*   **Full Decision Authority:** Executes trades and manages operations without requiring individual approvals for defined phases.
*   **Dust Consolidation:** Capable of sweeping small balances ('dust') from multiple sources into a primary holding currency (e.g., USDT).
*   **Automated DCA Execution:** Implements Dollar-Cost Averaging (DCA) strategies when specified market dips occur.
*   **Unified Balance Auditing:** Pulls and reports real-time, consolidated balance sheets across all connected exchanges.
*   **Credential Vault Management:** Manages access to multiple exchange credentials securely within a dedicated vault structure.

## Example Use Cases
1. **Executing Phase 1 Dust Sweep:** Instruct the agent to immediately sweep small residual balances from both primary and secondary Binance accounts into USDT for immediate liquidity.
2. **Monitoring Dip Conditions:** Set up triggers so that when BTC drops by X% within a specified timeframe, the agent automatically initiates the pre-planned DCA purchase on the Secondary account.
3. **Comprehensive Audit:** Request a 'PORTFOLIO SNA' report to get a single, unified view of total assets across Binance.US, Gemini, and Base EVM wallets for end-of-day reconciliation.