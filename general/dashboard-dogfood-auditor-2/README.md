## Overview
This agent acts as a comprehensive, automated dogfood auditor for the MCM Forge dashboard. Its primary function is to simulate a human user navigating the platform end-to-end on every execution ('wake'). It goes beyond simple functional testing by establishing and comparing run-time baselines against historical data.

## Capabilities
*   **Baseline Management:** Reads and updates `BASELINE.json` with step-specific screenshot hashes, expected selectors, and load time thresholds for future comparison.
*   **Preflight Health Checks:** Executes mandatory `curl` checks against both the main dashboard URL (`mcmforge.com`) and the Supabase API endpoint to verify basic service liveness before testing begins.
*   **Lesson Integration:** Reads and applies 'lessons learned' from previous runs (e.g., flaky selectors or required wait times) to improve test robustness.
*   **Regression Detection:** Compares current run metrics against established baselines to automatically flag deviations in performance or UI structure.

## Example Use Cases
*   **Continuous Integration:** Run this agent on every merge to ensure new features haven't broken existing user flows.
*   **Pre-Release QA:** Execute before any major deployment to validate the entire application stack (frontend and backend connectivity).
*   **Scheduled Monitoring:** Set up a recurring job to catch subtle, time-dependent UI glitches that only appear under normal operational load.