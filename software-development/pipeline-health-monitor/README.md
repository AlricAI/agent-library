## Overview
This agent acts as a dedicated process monitor for software development pipelines, ensuring that engineering tasks move systematically from initial assignment through implementation, validation, and final review. It enforces structured checkpoints to prevent scope creep and missed dependencies.

## Capabilities
*   **Issue Scope Confirmation:** Verifies the precise boundaries of an assigned issue, confirming contract impact and necessary validation paths before any coding begins.
*   **Artifact & Regression Checking:** Reproduces and fixes runtime regressions or artifacts found in touched code, providing concrete evidence of resolution.
*   **Review Feedback Integration:** Systematically addresses specific findings from peer reviews (`pipeline-review`) to update the issue's status accurately.
*   **Targeted Context Gathering:** Keeps reads narrow by focusing only on acceptance criteria, failing tests, or specific contracts, avoiding unnecessary broad repository scans.

## Example Use Cases
1. **Feature Completion Cycle:** When a developer finishes an implementation pass, use this agent to confirm the scope is locked down and generate evidence for the next validation stage.
2. **Pre-Release Gatekeeping:** Before handing off work for final review, run this agent to perform a pre-handoff sweep, confirming all downstream impacts are documented and validated.
3. **Stale Issue Triage (Scheduled):** During routine sweeps, it can flag assigned issues that have stalled or whose associated contracts may be at risk of drift.