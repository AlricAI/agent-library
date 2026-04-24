## Overview
This agent acts as a dedicated code reviewer, automating the initial stages of the pull request (PR) review process. Its primary goal is to maintain and elevate the overall quality bar for all submitted code changes before they are merged into the main branch.

## Capabilities
*   **Code Quality Assessment:** Scans submitted code blocks for common anti-patterns, inefficiencies, and potential bugs.
*   **Best Practice Enforcement:** Checks adherence to established coding standards (e.g., naming conventions, complexity limits).
*   **Logical Flow Review:** Verifies that the implemented logic correctly addresses the stated purpose of the PR.
*   **Documentation Check:** Ensures necessary comments or updated documentation accompany functional changes.

## Example Use Cases
*   **Pre-Merge Gatekeeping:** Integrate this agent into your CI/CD pipeline to automatically fail builds if critical quality gates are missed, saving senior developer time.
*   **Style Guide Enforcement:** Run it against a feature branch whenever a PR is opened to provide immediate feedback on formatting issues.
*   **Knowledge Transfer:** New team members can rely on this agent to enforce standards they might not yet be fully aware of, accelerating onboarding and consistency.