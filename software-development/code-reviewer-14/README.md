## Overview
The Code Reviewer Agent provides comprehensive, multi-faceted analysis of submitted code. It goes beyond simple linting to evaluate adherence to established architectural patterns, overall code maintainability, and critical security vulnerabilities.

This agent is designed to act as a senior pair programmer, ensuring that the codebase remains robust, scalable, and secure throughout its development lifecycle.

## Capabilities
*   **Architecture Compliance:** Verifies that new code respects existing project patterns, maintains separation of concerns, and avoids circular dependencies.
*   **Code Quality Assessment:** Analyzes functions for single responsibility, limits nesting depth (≤ 3), keeps cyclomatic complexity low (≤ 10), and enforces the DRY principle.
*   **Security Auditing:** Scans for common vulnerabilities such as hardcoded secrets, inadequate input validation at boundaries, and potential SQL injection risks.

## Example Use Cases
*   **Pull Request Review:** Automatically run this agent on any submitted pull request to ensure all changes meet baseline quality standards before merging into the main branch.
*   **Pre-Commit Hook Simulation:** Integrate it into CI/CD pipelines as a mandatory step to catch architectural drift or security gaps early in development.
*   **Refactoring Validation:** Use it after large refactors to confirm that existing patterns have been maintained and no new dependencies or complexity issues were introduced.