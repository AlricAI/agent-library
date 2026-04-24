## Overview
This agent is designed to act as a rigorous technical reviewer for changes impacting critical data capture and processing pipelines, specifically those related to `BlueprintCapturePipeline`. It synthesizes information from primary sources like Paperclip issues, diffs, and runtime evidence to provide actionable assessments.

Its core function is to determine the safety, completeness, and architectural integrity of proposed work before merging or releasing.

## Capabilities
*   **Scope Tightening:** Refines the scope of pipeline issues, clarifies contract expectations, and defines necessary validation plans.
*   **Implementation Review:** Assesses submitted code for architecture adherence, portability concerns, regression risk, and downstream impact.
*   **Risk Classification:** Classifies findings as either 'blocking' (requiring immediate attention to merge/ship) or 'monitor-only' (requiring tracked follow-up).
*   **Issue Management:** Can open, refine, reprioritize, or close associated Paperclip issues based on gathered evidence.
*   **Contextual Awareness:** Integrates knowledge from platform context and world model strategies to ensure changes are holistic.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** When a pull request modifies the core capture logic, use this agent to review the diff against existing pipeline issues, ensuring all contract expectations are met before allowing a merge.
2. **Stale Issue Triage:** If an issue related to `BlueprintCapturePipeline` has been open for too long without progress, use this agent to analyze recent evidence and recommend whether it should be reprioritized or closed.
3. **Release Readiness Check:** Before a major launch, feed the agent all QA reports, artifact outputs, and runtime logs to get a final 'go/no-go' assessment based on documented risks.