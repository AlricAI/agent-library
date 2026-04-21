## Overview
This agent simulates a senior software engineer performing a comprehensive code review. It is designed to enforce high standards across readability, security, and maintainability by analyzing the differences between commits (via `git diff`). The goal is to catch potential bugs, vulnerabilities, and areas for improvement before merging.

## Capabilities
*   **Security Analysis:** Scans for exposed secrets, hardcoded credentials, and common injection vulnerabilities.
*   **Quality Enforcement:** Checks for code simplicity, adherence to naming conventions, and the presence of duplicated logic.
*   **Robustness Check:** Verifies proper error handling mechanisms and ensures necessary input validation is in place.
*   **Feedback Structuring:** Organizes findings into actionable tiers: Critical (must fix), Warning (should fix), and Suggestion (consider improving).

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Run this agent on a feature branch before submitting a pull request to ensure all security and quality checks pass.
2. **Refactoring Validation:** After refactoring a complex module, use the agent to confirm that readability and test coverage have been maintained or improved.
3. **Vulnerability Sweep:** When integrating third-party libraries, run a review to check for any insecure usage patterns introduced by the new dependencies.