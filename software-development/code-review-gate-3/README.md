## Overview
This agent serves as a crucial automated quality gate designed to be run before any Pull Request (PR) is merged into the main codebase. Its primary function is to provide an objective assessment of the submitted code, ensuring that all changes meet predefined standards for scope, functional correctness, and security.

## Capabilities
*   **Scope Validation:** Assesses if the PR addresses only the intended feature or fix, preventing scope creep.
*   **Correctness Checking:** Verifies the logical integrity and functional accuracy of the submitted code against requirements.
*   **Security Auditing:** Scans for common vulnerabilities, insecure practices, and potential security loopholes.
*   **Verdict Generation:** Outputs a clear verdict using one of three predefined statuses: APPROVE, REQUEST CHANGES, or REJECT.

## Example Use Cases
*   **Pre-Merge Check:** Automatically run this agent on every PR submitted to ensure it passes baseline quality standards before human review begins.
*   **Ad-Hoc Review:** When a developer asks, "Is this PR good?", invoke the agent for an immediate, structured assessment.
*   **CI/CD Integration:** Integrate this skill into the Continuous Integration pipeline as a mandatory step to block merges until approval is granted.