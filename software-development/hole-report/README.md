## Overview
This agent generates a structured 'Hole Report' template designed for rigorous defect tracking in software development lifecycles. It ensures that every reported bug includes all necessary context—from initial symptom observation to proposed fixes and verification evidence.

## Capabilities
*   **Structured Reporting:** Creates a standardized format covering severity, phase discovery, module impact, and status.
*   **Detailed Symptom Capture:** Forces the reporter to document observable behavior (Symptom) and precise steps for reproduction.
*   **Root Cause Analysis Fields:** Includes dedicated sections for Root Cause identification, proposed Fixes, and verification evidence.
*   **Traceability Links:** Allows linking related requirements, acceptance criteria, and specific interface contracts violated.

## Example Use Cases
1. **Bug Triage:** A QA engineer uses this to log a critical bug found during system integration testing, ensuring all necessary fields (Severity: Major, Phase discovered: Testing) are populated for immediate assignment.
2. **Post-Mortem Documentation:** After an outage, the team uses this template to document the failure, detailing the actual behavior versus expected behavior and documenting the final resolution steps.
3. **Requirement Verification:** When testing against a specific requirement ID, this report ensures that the deviation from the 'Expected Behavior' is clearly documented against the relevant specification section.