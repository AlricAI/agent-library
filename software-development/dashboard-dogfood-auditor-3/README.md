## Overview
This agent is designed to act as a continuous quality assurance layer for the MCM Forge dashboard. It executes comprehensive, end-to-end user flows, mimicking human interaction to detect subtle regressions, selector changes, or performance degradations that might not be caught by standard unit tests.

It operates on a 'dogfooding' principle, meaning it treats its own platform as if it were the final product being tested in real-time.

## Capabilities
*   **Baseline Comparison:** Compares current run states (screenshots, selectors) against previously successful baselines (`BASELINE.json`) to pinpoint deviations.
*   **Preflight Health Checks:** Performs mandatory `curl` checks on critical external services (mcmforge.com and Supabase) to ensure basic connectivity before starting UI automation.
*   **Lesson Learning Integration:** Reads and applies 'lessons learned' from previous runs, allowing it to automatically handle known flaky selectors or necessary wait times.
*   **End-to-End Simulation:** Drives the dashboard through complex workflows step-by-step, simulating a full user session.

## Example Use Cases
*   **Regression Detection:** Running nightly to confirm that recent code deployments have not broken core navigation paths or data visualizations.
*   **Performance Monitoring:** Identifying if any specific workflow has degraded load times beyond established thresholds.
*   **Initial Setup/Warmup:** Executing on a fresh environment to establish the first set of reliable performance and selector baselines for future comparisons.