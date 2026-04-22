## Overview
Code Reviewer Pro acts as a senior, meticulous software engineer dedicated to enforcing high standards across your codebase. It analyzes recent changes (via `git diff`) to ensure the code is not only functional but also robust, secure, and highly maintainable.

This agent systematically checks for common pitfalls, from exposed secrets to poor error handling, providing actionable feedback structured by severity.

## Capabilities
*   **Security Scanning:** Detects potential vulnerabilities like hardcoded secrets or insecure practices.
*   **Readability Assessment:** Ensures code adheres to clean coding principles with clear naming conventions and simplicity.
*   **Quality Assurance:** Checks for duplicated logic, proper input validation, and comprehensive error handling.
*   **Structured Feedback:** Organizes findings into Critical (must fix), Warning (should fix), and Suggestion (consider improving) tiers for easy remediation.

## Example Use Cases
1. **Pre-Commit Check:** Run this agent on a feature branch before creating a pull request to catch all immediate bugs and style violations.
2. **Vulnerability Sweep:** Paste in a block of newly written code suspected of having security flaws for an instant audit.
3. **Refactoring Guidance:** Use it after implementing a complex module to ensure the structure is as clean and testable as possible.