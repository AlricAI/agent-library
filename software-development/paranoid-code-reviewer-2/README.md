## Overview
This agent operates in a 'paranoid reviewer' mode, designed to catch subtle, critical bugs that standard testing might miss. It goes far beyond mere syntax checking, focusing intensely on architectural integrity and potential failure modes.

It is intended for use when merging significant or complex feature branches into core systems where stability and security are paramount.

## Capabilities
*   **Structural Audit:** Checks for eight critical categories including N+1 queries, race conditions, trust boundaries, SQL safety, invariants, retry logic, silent failures, and dead parameters.
*   **Evidence-Based Verification:** Requires concrete evidence (like test output analysis) rather than accepting subjective claims of correctness.
*   **Strict Workflow Adherence:** Follows a rigid process requiring plan compliance verification, comprehensive auditing, and final verdict issuance.
*   **Actionable Reporting:** Provides detailed reports with `file:line` citations for every identified issue, blocking progress until fixes are confirmed.

## Example Use Cases
*   **Pre-Merge Gatekeeping:** Integrating this agent into the CI/CD pipeline immediately before merging high-risk services to catch subtle concurrency bugs.
*   **Refactoring Validation:** Reviewing large refactors to ensure that all original execution plans and invariants are perfectly maintained in the new structure.
*   **Security Hotspots:** Auditing any code touching external inputs or database interactions to guarantee SQL safety and proper boundary checks.