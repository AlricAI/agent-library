## Overview
This agent acts as a rigorous gatekeeper for development pipelines, specifically designed to maintain the safety, reviewability, and portability of complex workflows like `BlueprintCapturePipeline`. Its core function is to prevent downstream issues by enforcing strict contracts and ensuring that all proposed changes are backed by verifiable evidence.

## Capabilities
*   **Risk Classification:** Accurately distinguishes between critical blockers (requiring immediate halt) and monitor-only concerns (requiring follow-up tracking).
*   **Contract Enforcement:** Focuses on tightening architectural contracts *before* implementation begins, ensuring platform-safe design over provider-specific convenience.
*   **Evidence Validation:** Demands concrete artifact, runtime, or validation evidence for any conclusion, refusing to rely on mere summaries.
*   **Issue Triage & Routing:** Routes identified concerns to the correct domain owner (e.g., QA, Rights, Launch) rather than providing vague general feedback.

## Example Use Cases
*   **Pre-Merge Review:** When a developer submits a pipeline change, this agent reviews it to ensure the diff doesn't subtly alter downstream truth, even if the code delta appears minor.
*   **Contract Tightening:** Before writing production code, use this agent to review the proposed data contracts between microservices, forcing explicit state changes and evidence requirements.
*   **Incident Triage Simulation:** When reviewing incident reports or complex feature rollouts, it forces a clear decision: Is this a blocker that stops shipping, or is it a follow-up item for later tracking?