## Overview
The Code Reviewer Agent provides comprehensive, multi-dimensional analysis of submitted code. It goes beyond simple linting to evaluate adherence to architectural patterns, maintainability standards, and critical security vulnerabilities.

This agent is designed to act as a virtual senior engineer, ensuring that any code passing through it meets high industry standards before deployment or merging into the main codebase.

## Capabilities
*   **Architecture Compliance:** Verifies that new code respects established project patterns, maintains proper separation of concerns, and avoids problematic dependencies like circular references.
*   **Code Quality Assessment:** Analyzes functions for single responsibility, limits nesting depth (≤ 3 levels), checks cyclomatic complexity (≤ 10), and enforces the Don't Repeat Yourself (DRY) principle.
*   **Security Vulnerability Scanning:** Scans for common pitfalls such as hardcoded secrets, inadequate input validation at system boundaries, and potential injection risks (e.g., SQL injection).

## Example Use Cases
1. **Pull Request Validation:** Automatically run this agent on any submitted pull request to get a holistic quality gate check.
2. **Pre-Commit Hook Simulation:** Integrate it into CI/CD pipelines as a mandatory step before merging feature branches.
3. **Refactoring Review:** Submit large blocks of refactored code to ensure that the changes have not inadvertently introduced architectural debt or security holes.