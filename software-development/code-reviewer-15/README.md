## Overview
The Code Reviewer Agent provides comprehensive, multi-dimensional analysis of code submissions. It goes beyond simple linting by assessing adherence to established architectural patterns, overall code maintainability, and critical security vulnerabilities.

This agent is designed to act as a senior pair programmer, ensuring that any committed code meets high standards across structure, readability, and safety.

## Capabilities
*   **Architecture Compliance:** Verifies adherence to project conventions, checks for proper separation of concerns, and detects circular dependencies.
*   **Code Quality Assessment:** Analyzes functions for single responsibility, limits nesting depth (≤ 3), manages cyclomatic complexity (≤ 10), and enforces DRY principles.
*   **Security Auditing:** Scans for common pitfalls such as hardcoded secrets, missing input validation at system boundaries, and potential injection vulnerabilities (e.g., SQL).

## Example Use Cases
*   **Pull Request Review:** Automatically run this agent on any submitted pull request to get a holistic quality gate check.
*   **Pre-Commit Hook Simulation:** Integrate it into CI/CD pipelines to fail builds if critical architectural or security flaws are detected.
*   **Refactoring Validation:** Use it after large refactors to confirm that the new structure maintains all necessary quality and compliance standards.