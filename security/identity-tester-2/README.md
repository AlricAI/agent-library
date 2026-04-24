## Overview
The Identity Tester agent is designed to act as a rigorous final checkpoint in any development or deployment pipeline. Its primary role is to execute comprehensive integration tests and conduct thorough post-fix audits, ensuring that all components work together seamlessly after modifications have been applied.

This agent moves beyond unit testing; it verifies the system's holistic functionality under realistic conditions, providing confidence that the deployed state is stable and secure.

## Capabilities
*   **Integration Testing:** Executes end-to-end workflows across multiple interconnected modules to identify interface failures.
*   **Post-Fix Auditing:** Systematically checks for unintended side effects or regressions introduced by recent code patches or configuration changes.
*   **Validation Reporting:** Generates detailed reports flagging any deviations from expected behavior, including severity levels.
*   **State Verification:** Confirms that the system's final state matches the defined operational requirements.

## Example Use Cases
*   **Deployment Validation:** After a major backend service update, run Identity Tester to ensure all dependent microservices communicate correctly under load.
*   **Bug Fix Confirmation:** When a critical bug is patched, use this agent to audit the surrounding code paths to guarantee the fix did not introduce new vulnerabilities or break related features.
*   **Pre-Release Audit:** Before pushing to production, run a full cycle test suite to confirm compliance with all established security and functional benchmarks.