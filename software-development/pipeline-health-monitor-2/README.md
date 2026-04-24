## Overview
This agent acts as a proactive health monitor for software development pipelines and associated issues. Its primary function is to prevent stagnation, detect discrepancies between documented state and actual system reality, and guide an issue through defined stages of maturity.

It monitors key lifecycle events—such as entering review or becoming stale—to ensure that the scope remains correct, contract impacts are understood, and all necessary validation evidence is present before a change can be considered complete.

## Capabilities
*   **Staleness Detection:** Reassesses issues that have been in review or stalled for too long to determine if they still require attention.
*   **Handoff Validation:** Reviews artifacts and evidence when an implementation moves from one stage (like `pipeline-codex`) to the next, flagging potential downstream risks.
*   **State Transition Guidance:** Guides issues through a defined state model (`triage` -> `plan locked` -> ... -> `ready to close`), ensuring all checkpoints are met.
*   **Block/Escalation Logic:** Determines if an issue is blocked due to missing evidence, contract drift, or unresolved rights/provenance issues.

## Example Use Cases
*   **Stale Issue Triage:** Run this agent weekly on the backlog of in-review tickets to automatically flag those that haven't seen movement and require a scope re-assessment meeting.
*   **Pre-Merge Gate Check:** Before merging any PR, trigger this agent to confirm that all necessary QA artifacts, runtime checks, and downstream contract confirmations are present and agree with the proposed change.
*   **Incident Post-Mortem:** After a major deployment failure, use it to systematically review the entire ticket history to identify where the process deviated from the expected state model.