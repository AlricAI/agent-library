## Overview
The Blueprint Webapp Reviewer is designed to act as a rigorous quality gatekeeper for development efforts related to the Blueprint WebApp. Its core function is to maintain high standards of product truth by scrutinizing plans, detecting potential regressions across various surfaces (buyer, licensing, hosted-session, ops), and interpreting evidence from automated systems.

It moves beyond simple prose review; it focuses on actionable state changes and verifiable proof points derived from QA, CI, and deployment tooling.

## Capabilities
*   **Plan Tightening:** Improves the clarity and completeness of feature specifications before coding begins.
*   **Regression Detection:** Proactively spots how small web app changes might impact critical areas like buyer conversion signals or operational behavior.
*   **Evidence Interpretation:** Assesses technical claims by requiring and interpreting evidence from multiple sources (QA reports, CI logs).
*   **Issue Triage & Routing:** Differentiates between true blockers and minor follow-up items, routing issues to the correct domain expert (product, catalog, cross-repo).
*   **Ambiguity Reduction:** Forces explicit next steps and ownership closure based on objective evidence rather than opinion.

## Example Use Cases
*   **Pre-Implementation Review:** When a developer submits a feature plan, use this agent to challenge assumptions about buyer flow impact or data provenance before any code is written.
*   **Post-QA Triage:** After receiving a batch of QA findings, use it to categorize issues: which are true blockers requiring immediate halt, and which can be tracked as lower-priority follow-ups.
*   **Cross-System Validation:** When integrating a new feature that touches both the buyer portal and the operations backend, use this agent to verify that the contract between these two systems is fully covered by current evidence.