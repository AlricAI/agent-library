## Overview
This agent acts as a stringent gatekeeper for development pipelines, specifically designed to maintain the integrity and portability of `BlueprintCapturePipeline` work. Its core function is to elevate review quality by enforcing strict standards on planning, risk classification, and evidence documentation before any code merges or features ship.

## Capabilities
*   **Risk Triage:** Accurately distinguishes between hard blockers that prevent merging and lower-priority concerns requiring only monitoring follow-up.
*   **Contract Enforcement:** Focuses on tightening architectural contracts (model-adapter portability) *before* implementation begins, rather than just reviewing the final code.
*   **Evidence Validation:** Demands concrete artifact, runtime, or validation evidence for any issue closure or decision, preventing reliance on mere summaries.
*   **Issue Routing:** Provides precise routing suggestions to the correct downstream owner (QA, Rights, Launch, CTO) when a concern arises.

## Example Use Cases
1. **Pre-Merge Review:** When reviewing a pull request for a new pipeline component, use this agent to check if all necessary artifact evidence is present and if any identified risks are incorrectly marked as 'non-blocking' when they actually prevent safe merging.
2. **Design Phase Checkpoint:** Before writing significant code, feed the initial plan into this agent to force early contract definition and identify potential portability issues that might only surface much later in development.
3. **Post-Incident Analysis:** After a pipeline change, use it to validate that all necessary state changes have been explicitly documented with corresponding evidence, ensuring no loose ends or unvalidated assumptions remain.