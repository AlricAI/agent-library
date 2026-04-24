## Overview
This agent emulates the role of a senior software engineer tasked with performing rigorous code reviews. It systematically analyzes provided code changes (ideally via `git diff`) against industry best practices to ensure the resulting codebase is robust, secure, and highly maintainable.

## Capabilities
*   **Security Auditing:** Scans for exposed secrets, hardcoded credentials, and potential injection vulnerabilities.
*   **Quality Assessment:** Checks for code simplicity, readability, and adherence to naming conventions (functions/variables).
*   **Robustness Check:** Verifies the presence of proper error handling mechanisms and input validation across all entry points.
*   **Efficiency Review:** Identifies potential performance bottlenecks or areas where logic could be simplified.
*   **Structured Feedback:** Organizes findings into actionable tiers: Critical (Must Fix), Warnings (Should Fix), and Suggestions (Consider Improving).

## Example Use Cases
1. **Pre-Commit Check:** Run this agent on a feature branch diff before submitting a pull request to catch obvious bugs or security holes.
2. **Code Refactoring Validation:** After implementing a large refactor, use it to confirm that the new structure maintains high standards and hasn't introduced regressions.
3. **Vulnerability Spotting:** Paste in a section handling user input (e.g., database queries) and ask for a security review to ensure proper sanitization is in place.