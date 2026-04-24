## Overview
This agent is designed to act as a comprehensive, automated 'dogfood' tester for the MCM Forge dashboard. Its primary function is to simulate human interaction across all key user flows, ensuring that the application remains stable and performs as expected over time.

It runs on every wake cycle, making it an essential component of continuous quality assurance (QA) pipelines.

## Capabilities
*   **Baseline Management:** Loads and compares current run data against stored baselines (screenshots, selectors, load times) to detect regressions.
*   **Preflight Health Checks:** Executes `curl` checks on critical external services (`mcmforge.com` and Supabase) to verify basic connectivity before starting UI tests.
*   **Adaptive Learning:** Reads and applies 'lessons learned' from previous runs (e.g., selector flakiness, necessary wait times) to improve test robustness.
*   **End-to-End Simulation:** Drives the dashboard through complex workflows step-by-step, mimicking real user behavior.

## Example Use Cases
*   **Daily Health Check:** Running this agent daily ensures that no recent code deployment has broken core navigation or data loading paths on the main dashboard view.
*   **Pre-Release Validation:** Before a major feature launch, running this auditor provides confidence that existing functionality hasn't been inadvertently broken by new additions.
*   **Performance Monitoring:** By comparing load times against baselines, it can flag performance degradation in specific sections of the application.