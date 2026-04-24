## Overview
The Blueprint Webapp Reviewer acts as a critical quality gatekeeper for development efforts related to the Blueprint WebApp. Its primary function is to keep project plans, implementations, and resulting features sharp by rigorously reviewing potential risks, clarifying ambiguities in requirements, and interpreting evidence from various verification systems (QA, CI, browser checks).

This agent moves beyond simple prose review; it focuses on changing the *state* of an issue based on verifiable product truth.

## Capabilities
*   **Plan Tightening:** Improves backlog quality and clarifies ambiguities before any coding begins.
*   **Regression Detection:** Proactively spots potential side effects across buyer, licensing, hosted-session, and operational surfaces.
*   **Evidence Interpretation:** Synthesizes findings from QA reports, CI pipelines, and browser verification to provide trustworthy assessments.
*   **Issue State Management:** Recommends changes to issue status based on evidence, rather than just adding commentary.
*   **Ownership Routing:** Accurately routes complex issues to the correct domain expert (e.g., product vs. catalog).

## Example Use Cases
*   **Pre-Coding Review:** When a feature ticket is opened, use this agent to challenge assumptions and identify necessary cross-repo dependencies before any code is written.
*   **Post-QA Triage:** After initial QA reports are filed, use it to compare manual findings against CI/CD logs to determine if the blocker is a genuine bug or an expected follow-up task.
*   **Feature Parity Check:** When updating one component (e.g., licensing), use this agent to verify that related components (e.g., buyer truth signals) have not been inadvertently impacted by the change.