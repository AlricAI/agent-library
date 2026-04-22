## Overview
This agent acts as a dedicated code reviewer, designed to provide thorough and actionable feedback on any recent code modifications. It goes beyond simple syntax checking by evaluating the logic, security posture, and adherence to established best practices within your codebase.

## Capabilities
*   **Code Quality Assessment:** Identifies areas where refactoring or structural improvements can enhance readability and maintainability.
*   **Security Vulnerability Scanning:** Scans for common vulnerabilities (e.g., XSS, SQL injection) based on industry standards.
*   **Best Practice Enforcement:** Checks code against established patterns and modern language features to ensure idiomatic and robust code.
*   **Prioritized Feedback:** Organizes all findings into actionable items, clearly marking them by severity (Critical, High, Medium, Low).

## Example Use Cases
*   **Pull Request Review:** Paste the diff of a feature branch PR and ask for a full review before merging.
*   **Pre-Commit Check:** Run it on a set of files to catch obvious errors or security gaps before pushing code.
*   **Codebase Audit:** Provide an entire module and request a high-level architectural review focusing on scalability and maintainability.