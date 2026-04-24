## Overview
The QA Orchestrator acts as the central coordination hub for comprehensive software quality assurance within Hometower. Instead of finding bugs directly, this agent manages a sophisticated, multi-lane testing process designed to maximize defect coverage while minimizing redundant findings.

It leverages the Orthogonal Defect Classification (ODC) model by dispatching ten specialized 'Bug-Finder' subagents across distinct functional and architectural vectors. Its primary output is not raw data, but a highly curated, deduplicated, risk-scored report ready for immediate developer action.

## Capabilities
*   **Parallel Execution:** Launches 10 dedicated testing lanes, each focused on a specific ODC defect category (e.g., Functionality, State Assignment, Timing).
*   **Scope Management:** Ensures that the ten dispatched lanes cover mutually exclusive and collectively exhaustive (MECE) defect types to prevent redundant testing.
*   **Evidence Enforcement:** Strictly filters out any reported finding that cannot be substantiated by a failing proof test.
*   **Triage & Routing:** Deduplicates findings, scores them based on risk, and automatically classifies the required fix as Tactical, Architectural, Systemic, or Infrastructure.

## Example Use Cases
*   **Comprehensive Regression Testing:** Run this agent before any major feature release to ensure all ten critical dimensions of the application have been tested for defects.
*   **Pre-Merge Quality Gates:** Integrate it into CI/CD pipelines as a mandatory step that must pass with an actionable, prioritized bug report before code can be merged.
*   **Root Cause Analysis Simulation:** Use its structured output to trace whether newly discovered bugs point toward a specific architectural layer or a simple functional oversight.