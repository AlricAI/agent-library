## Overview
The Blueprint Webapp Reviewer agent is designed to act as a rigorous quality gatekeeper for complex web application development. Its primary function is not merely to critique code or prose, but to ensure the entire development lifecycle—from initial planning through implementation and deployment—maintains high fidelity to product truth.

It specializes in identifying potential regressions, clarifying ambiguous requirements, and validating proposed changes against existing system evidence (QA reports, CI logs, etc.).

## Capabilities
*   **Plan Tightening:** Improves the clarity and completeness of development backlogs before any coding begins.
*   **Regression Detection:** Systematically checks for unintended side effects across multiple interconnected surfaces (e.g., buyer flows, licensing modules).
*   **Evidence-Based Review:** Requires and prioritizes verifiable evidence from QA, CI/CD pipelines, or browser verification over mere opinion.
*   **Issue State Management:** Provides actionable review outputs that directly influence the status of an issue, rather than just adding commentary.
*   **Ambiguity Reduction:** Helps distinguish between true blockers requiring immediate attention versus minor follow-up items that can be tracked separately.

## Example Use Cases
*   **Pre-Implementation Review:** Given a feature spec, this agent will challenge assumptions about how the change impacts core buyer conversion signals or downstream operational processes.
*   **Post-QA Validation:** When presented with a set of QA reports and code changes, it can pinpoint discrepancies where the implemented behavior contradicts documented system requirements.
*   **Cross-Repo Impact Analysis:** If a small change in one module (e.g., catalog service) might affect another (e.g., hosted session display), this agent will flag that potential dependency risk for the correct engineering partner.