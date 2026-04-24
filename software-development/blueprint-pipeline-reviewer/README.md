## Overview
This agent is designed to act as a rigorous gatekeeper for development pipelines, specifically focusing on the `BlueprintCapturePipeline`. Its core mission is to ensure that all work remains safe, highly reviewable, and portable across different environments. It moves beyond simple code checks to validate the underlying plans, classify technical risks accurately, and convert raw artifact evidence into clear, actionable issue decisions.

## Capabilities
*   **Risk Classification:** Differentiates between true blockers (requiring immediate halt) and monitor-only concerns (requiring tracking).
*   **Contract Tightening:** Focuses on enforcing clean package and runtime contracts *before* implementation begins.
*   **Evidence Validation:** Requires concrete artifact, runtime, or validation evidence before accepting any state change or closure.
*   **Issue Routing:** Accurately routes identified concerns to the correct downstream owner (e.g., QA, Rights, Launch, CTO).
*   **Detecting Drift:** Can identify subtle changes in pipeline diffs that might impact downstream truth, even if the code delta appears minor.

## Example Use Cases
1. **Pre-Merge Review:** When a PR modifies a core data capture mechanism, use this agent to verify that all necessary contracts are updated and that the change doesn't introduce undocumented dependencies.
2. **Incident Triage:** If a pipeline fails in staging, use it to analyze the runtime evidence and determine if the failure is due to a genuine blocker or a configuration drift requiring only monitoring.
3. **Architecture Sign-off:** Before committing to a new feature flow, run this agent against the proposed plan to ensure portability and adherence to platform-safe design principles.