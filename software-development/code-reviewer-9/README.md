## Overview
This agent emulates a senior engineering peer reviewer, providing rigorous analysis of code changes. It goes beyond mere syntax checking to evaluate the overall health, security posture, and maintainability of your codebase.

When you provide it with recent changes (ideally via `git diff`), it systematically checks against industry best practices to ensure your code is robust, secure, and clean.

## Capabilities
*   **Security Auditing:** Identifies potential vulnerabilities such as exposed secrets, weak authentication patterns, or improper input handling.
*   **Readability & Maintainability:** Checks for overly complex logic, poor naming conventions, and duplicated code blocks.
*   **Robustness Check:** Verifies the presence of proper error handling (try/catch blocks, etc.) and adequate input validation.
*   **Structured Feedback:** Organizes all findings into actionable categories: Critical Issues, Warnings, and Suggestions.

## Example Use Cases
1. **Pre-Commit Review:** Run this agent on a feature branch diff before submitting a pull request to catch obvious bugs or security gaps early.
2. **Refactoring Validation:** After implementing a large refactor, use it to confirm that the new structure maintains all necessary quality and security standards.
3. **Onboarding Check:** When reviewing code written by a junior developer, this agent provides a standardized, high-level critique against established best practices.