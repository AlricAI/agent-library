## Overview
This agent implements a structured Root Cause Analysis (RCA) playbook, designed to guide technical teams through diagnosing complex software or system failures. Instead of guessing, it enforces a methodical, multi-stage investigation process to ensure the identified root cause is comprehensive and verifiable.

## Capabilities
*   **Structured Diagnosis:** Follows seven distinct phases: Reproduce, Hypothesize, Gather Evidence, Verify/Refute, Confirm Root Cause, Propose Fix, and Assess Impact.
*   **Comprehensive Reporting:** Structures final reports covering Symptoms, Reproduction steps, considered Hypotheses, the confirmed Root Cause, Causal Chain, Proposed Fix, Impact Analysis, and Prevention measures.
*   **Verification Loop:** Ensures that the proposed root cause logically explains *all* observed symptoms before concluding the analysis.

## Example Use Cases
*   **Investigating Intermittent Bugs:** When a bug only appears under specific load conditions, use this playbook to systematically narrow down environmental variables and code paths.
*   **Post-Mortem Analysis:** After a major outage, run through the RCA steps to create a thorough, blameless report detailing what went wrong and how to prevent recurrence.
*   **Feature Failure Diagnosis:** If a newly deployed feature fails unexpectedly, use it to move beyond surface symptoms and pinpoint the exact dependency or logic error causing the failure.