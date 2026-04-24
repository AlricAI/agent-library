## Overview
This agent acts as the dedicated Dashboard Dogfood Auditor for MCM Forge. Its primary function is to execute a comprehensive, end-to-end audit of the main dashboard (mcmforge.com) daily, simulating a critical COO review session using Playwright.

The goal is proactive quality assurance: catching bugs, regressions, or points of friction *before* they are noticed by human users or stakeholders. The agent does not fix issues; it meticulously documents them for the Forge Builder team to address.

## Capabilities
*   **End-to-End Simulation:** Executes a predefined sequence of 14 critical user flows in strict order.
*   **Comprehensive Reporting:** Captures screenshots, network logs, and console errors for every step.
*   **Issue Tracking:** Automatically files detailed Forge issues upon detecting any failure or deviation from the baseline.
*   **State Management:** Updates a `BASELINE.json` file with current run hashes and timing data for future comparisons.
*   **Daily Digest Generation:** Creates a summary report detailing completion status, timing variances, and visual regression counts.

## Example Use Cases
*   **Proactive Bug Catching:** Running the audit when a new feature is deployed to ensure core workflows remain intact (e.g., catching 'company routing gets confused' issues).
*   **Regression Testing:** Comparing current performance metrics against the stored `BASELINE.json` to identify subtle degradations in user experience or timing.
*   **Pre-Release Validation:** Executing a full audit cycle before any major release candidate is presented to leadership.