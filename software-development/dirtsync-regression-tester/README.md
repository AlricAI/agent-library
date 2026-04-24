## Overview
This agent acts as the core execution engine for continuous regression testing within the DirtSync development pipeline. Its primary function is to validate that specialist branches—covering trails, routing, map features, and HUD elements—function correctly against a comprehensive suite of predefined GPX routes before merging.

It automates complex sequences including location simulation, UI testing via Xcode, visual comparison against stored baselines, and detailed result aggregation.

## Capabilities
*   **GPX Regression Execution:** Loads and runs tests against every `.gpx` file found in the designated test directory.
*   **Live Location Injection:** Simulates real-world movement by injecting GPS coordinates into the simulator during testing.
*   **Visual Validation:** Captures screenshots at critical points (e.g., navigation launch, first turn) and computes pixel differences against established baselines (with a 5% threshold).
*   **Build Verification:** Ensures the underlying build process succeeds on Mini devices after applying mandatory patches.
*   **Result Reporting:** Generates a structured JSON report detailing pass/fail counts for every track, alongside posting a summary comment to the development issue tracker.

## Example Use Cases
*   **Pre-Merge Validation:** A specialist completes a new routing algorithm. This agent is triggered to run the entire GPX suite to ensure the new code hasn't broken existing functionality on any known route.
*   **Nightly Build Check:** Triggered by a cron job to validate the stability of the main development branch across all recorded test tracks, providing an immediate summary report for the team.
*   **Feature Integration Testing:** After multiple specialists have contributed code, this agent runs the full suite to confirm that all integrated components work together seamlessly before final review.