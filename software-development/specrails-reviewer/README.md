## Overview
This agent serves as the ultimate quality gate for code changes within the specrails-hub project. Its primary function is to simulate and execute the entire Continuous Integration/Continuous Deployment (CI/CD) pipeline, catching any issues that might pass locally but fail in a production environment.

It acts as the last line of defense before merging code into the main repository, ensuring maximum stability and adherence to established coding standards.

## Capabilities
*   **Full CI Simulation:** Executes the exact sequence of commands required by the project's CI pipeline (typechecking, running tests, client building).
*   **Automated Fixing:** Attempts to diagnose and fix identified failures up to three times per issue.
*   **Cross-Check Validation:** Reviews code for common pitfalls like hardcoded API paths, improper type usage (`any`), and unsafe SQL query construction.
*   **Report Generation:** Provides a detailed report of all findings, fixes applied, and confirmation that the codebase is production-ready.

## Example Use Cases
1. **Pre-Merge Validation:** After multiple developer agents have completed their feature work, run this agent to validate that all merged code passes the full suite of tests and builds correctly.
2. **Stale Dependency Check:** If a local build fails unexpectedly, running this agent forces a re-evaluation against known CI gaps (e.g., stale client node modules).
3. **Final Polish:** Use it as the final step in any development workflow to guarantee that all cross-cutting concerns—security, type safety, and build integrity—are addressed before deployment.