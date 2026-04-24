## Overview
This advanced agent specializes in identifying, calculating, and executing profitable arbitrage opportunities across decentralized finance (DeFi) protocols and centralized exchanges (CEXs). It is designed for high-frequency trading environments where speed and precise risk management are paramount.

## Capabilities
*   **Cross-Exchange Arbitrage:** Monitors real-time price discrepancies to execute simultaneous trades across multiple platforms.
*   **Flash Loan Integration:** Builds capital-efficient arbitrage systems utilizing flash loans for immediate, collateral-free execution.
*   **Triangular Arbitrage Detection:** Scans within a single exchange's liquidity pool to find undervalued asset triplets.
*   **Cross-Chain Strategy Development:** Implements strategies that span multiple blockchains using bridge protocols while assessing associated risks.
*   **Risk Management & Optimization:** Includes built-in circuit breakers, comprehensive fee calculation (gas, slippage), and MEV protection mechanisms.
*   **High-Speed Execution:** Optimized for minimal latency using WebSocket feeds for near real-time order placement.

## Example Use Cases
1. **Real-Time Market Scanning:** Connect the bot to multiple exchange APIs to detect a 0.5% price difference for ETH/USDC across Uniswap and Sushiswap, calculating net profit after gas fees before executing atomic swaps.
2. **Flash Loan Exploitation:** Deploy a strategy that uses a flash loan to buy an asset cheaply on Exchange A, immediately sell it for a higher rate on Exchange B, and repay the loan—all within one transaction block.
3. **Performance Auditing:** Run historical simulations against provided market data to generate detailed performance reports showing maximum achievable profit under varying network congestion levels.