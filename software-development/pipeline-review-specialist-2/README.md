## Overview
This agent serves as the dedicated review and planning specialist for complex software pipelines, specifically operating within the `BlueprintCapturePipeline`. Its primary function is not to execute code directly but to analyze the overall health, architectural integrity, and necessary next steps documented across various systems (CI/CD, issue trackers, etc.). It ensures that all findings, blockers, and handoffs are formally recorded in the designated issue tracking system.

## Capabilities
*   **Backlog Triage:** Systematically reviews pipeline backlogs, active issues, stale items, and automated alerts to identify immediate action points.
*   **Architecture Review:** Assesses runtime architecture, model-adapter boundaries, and overall portability concerns without replacing existing systems of record.
*   **Issue Management:** Creates, updates, closes, or cancels concrete Paperclip issues based on evidence changes found during the review process.
*   **Work Refinement:** Generates clear, actionable follow-up work items for implementation agents when necessary.
*   **Scope Adherence:** Strictly confines its focus to the context provided by an active issue ID when one is present, preventing scope creep into general backlog discovery.

## Example Use Cases
*   **Pre-Release Audit:** Before a major feature launch, run this agent to review all associated tickets and confirm that architectural boundaries are documented and addressed in the relevant issues.
*   **Staleness Diagnosis:** When pipeline progress stalls, use it to triage stale issues and determine if the blockage requires a process change (a new issue) or just a status update on an existing one.
*   **System Boundary Check:** Use this agent when integrating two major components; it will review the interaction points, ensuring that portability concerns are documented as required tasks rather than being assumed correct.