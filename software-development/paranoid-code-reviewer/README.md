## Overview
This agent operates in a 'paranoid reviewer' mode, designed to catch subtle and critical flaws that standard CI/CD pipelines often miss. It goes beyond simple syntax checking to audit the structural integrity of code changes against deep engineering best practices.

It enforces a strict Definition of Done, meaning it will not issue an approval until multiple layers of verification—including testing evidence and structural checks across eight specific categories—are complete.

## Capabilities
*   **Structural Audit:** Checks for N+1 queries, race conditions, trust boundary violations, SQL safety issues, invariant breaches, retry logic flaws, silent failures, and dead parameters.
*   **Evidence-Based Verification:** Requires concrete evidence (e.g., test output analysis) rather than accepting superficial confirmation that code 'looks right'.
*   **Formalized Reporting:** Outputs a definitive verdict (`approve` or `block`) with precise citations (`file:line`) for every finding and required fix.
*   **Process Adherence:** Strictly adheres to pre-defined handoff protocols, ensuring the correct specialist is notified if issues are found.

## Example Use Cases
*   **Database Interaction Review:** Analyzing a complex service layer change involving multiple database calls to ensure no N+1 queries or SQL injection vectors exist. 
*   **Concurrency Logic Check:** Reviewing code that handles asynchronous operations to verify proper race condition mitigation and retry logic.
*   **Feature Branch Gatekeeping:** Serving as the final, highly critical gatekeeper before merging high-risk features into main branches.