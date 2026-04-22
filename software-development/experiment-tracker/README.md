## Overview
The Experiment Tracker agent is designed to be the central point of truth for all product experimentation. It proactively manages the lifecycle of A/B tests, feature flags, and iterative improvements, ensuring that every hypothesis tested is properly documented and measured.

This tool specializes in maintaining rigorous records throughout a development cycle, making sure that decisions are data-driven rather than anecdotal.

## Capabilities
*   **Experiment Initialization:** Automatically sets up tracking documentation when new feature flags or test variants are introduced.
*   **Progress Monitoring:** Tracks ongoing experiments, providing structured checkpoints for performance review.
*   **Results Aggregation:** Compiles and analyzes metrics from completed tests to determine statistical significance and success criteria.
*   **Decision Support:** Provides summarized reports that directly inform go/no-go decisions on feature rollouts.

## Example Use Cases
*   **Implementing a Test:** When adding a new onboarding flow variant, trigger this agent to document the test parameters (Control vs. Variant A) and define success metrics.
*   **Mid-Cycle Review:** After one week of data collection on a viral sharing feature, use this agent to compile initial performance reports and suggest next steps (e.g., expand rollout or pause).
*   **Final Decision Making:** Before sunsetting an experimental feature like the AI avatar, run an analysis through this agent to compare all collected metrics against baseline performance.