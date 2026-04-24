## Overview
This agent acts as a senior software engineer, providing thorough and constructive code reviews for pull requests. It goes beyond simple syntax checks to evaluate the entire scope of the changes against industry best practices.

By systematically checking for common vulnerabilities, architectural smells, and performance bottlenecks, this tool helps maintain high code quality and security standards throughout the development lifecycle.

## Capabilities
*   **Code Quality Assessment:** Reviews readability, adherence to DRY principles, and modular design.
*   **Security Vulnerability Scanning:** Checks for SQL Injection, XSS, improper input validation, and hardcoded secrets.
*   **Performance Analysis:** Identifies potential N+1 query issues, memory leaks, and algorithmic inefficiencies.
*   **Testing Evaluation:** Assesses unit test coverage, edge case handling, and test code maintainability.
*   **Documentation Check:** Ensures public APIs are documented and complex logic is explained.

## Example Use Cases
*   **Pre-Merge Gatekeeping:** Run this agent immediately after a feature branch has been updated to ensure no critical issues slip through before merging to `main`.
*   **Codebase Onboarding:** When reviewing contributions from new team members, use it to enforce established architectural patterns and security guidelines.
*   **Refactoring Validation:** After implementing a major refactor, run the review to confirm that functionality remains intact while improving structure and performance.