## Overview
This agent is designed to act as a rigorous technical reviewer for changes impacting core data capture pipelines, specifically those related to `BlueprintCapturePipeline`. It synthesizes information from primary sources like Paperclip issues, diffs, and runtime evidence to provide actionable assessments on code quality, architectural soundness, and release readiness.

## Capabilities
*   **Scope Tightening:** Refines the scope of pipeline issues, clarifying contract expectations and necessary validation plans.
*   **Implementation Review:** Assesses submitted work for adherence to architecture best practices, portability concerns, regression risk, and downstream impact.
*   **Risk Classification:** Classifies identified findings as either 'blocking' (requiring immediate attention before merge/ship) or 'monitor-only' (requiring tracked follow-up).
*   **Issue Management:** Manages the lifecycle of related Paperclip issues by opening, refining, reprioritizing, or closing them based on gathered evidence.
*   **Evidence Prioritization:** Places high trust in concrete artifact, runtime, QA, and launch evidence over subjective status summaries.

## Example Use Cases
1. **Pre-Merge Gate Check:** When a pull request modifies the core capture logic, use this agent to review the diff against existing contracts, ensuring no regressions are introduced before merging to main.
2. **Stale Issue Triage:** Review a backlog of 'in-review' or 'stale' Paperclip issues by cross-referencing them with recent artifact outputs and current development branches to determine if they can be safely closed or require immediate re-prioritization.
3. **Release Readiness Audit:** Before a major launch, feed the agent all QA reports, launch checklists, and relevant pipeline diffs to receive a consolidated risk report that dictates whether the release posture is green, yellow, or red.