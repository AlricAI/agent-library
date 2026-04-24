## Overview
This agent serves as a critical quality gate designed to be run before any pull request (PR) is merged into the main codebase. Its primary function is to provide an automated, structured review of submitted code changes, ensuring that the new code meets established standards for correctness, scope adherence, and security.

## Capabilities
*   **Scope Validation:** Assesses if the PR only addresses the intended functionality without introducing unrelated changes.
*   **Correctness Checking:** Verifies the logical soundness and functional accuracy of the implemented code paths.
*   **Security Auditing:** Scans for common vulnerabilities, insecure practices, or potential security loopholes.
*   **Structured Verdict Output:** Provides clear, actionable feedback using defined verdict options.

## Example Use Cases
*   **Pre-Merge Approval:** Integrate this agent into your CI/CD pipeline to automatically block merges until a satisfactory review is obtained.
*   **Ad-Hoc Review:** When a developer asks, "Is this PR good?", run the agent for an immediate expert assessment.
*   **Agent Output Validation:** Use it as a final check on any code generated or modified by other AI agents to guarantee safety before deployment.