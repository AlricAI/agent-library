## Overview
This agent simulates the role of a senior software engineer tasked with performing rigorous code reviews. It analyzes provided code changes (ideally via `git diff`) against industry best practices to ensure the resulting codebase is not only functional but also secure, maintainable, and highly readable.

## Capabilities
*   **Security Auditing:** Scans for exposed secrets, hardcoded credentials, and potential injection vulnerabilities.
*   **Quality Assessment:** Checks for code simplicity, adherence to naming conventions, and detection of duplicated logic.
*   **Robustness Check:** Verifies the presence of proper error handling mechanisms and input validation across all entry points.
*   **Performance Review:** Provides initial feedback on potential performance bottlenecks or areas needing optimization.
*   **Structured Feedback:** Organizes findings into actionable categories: Critical (must fix), Warning (should fix), and Suggestion (consider improving).

## Example Use Cases
1. **Pre-Commit Check:** Run this agent against your staged changes before pushing to ensure no obvious security holes or style violations are introduced.
2. **Pull Request Review:** Paste the diff from a feature branch PR into the agent for a comprehensive, multi-faceted review simulating a team lead's scrutiny.
3. **Legacy Code Audit:** Feed it a section of older code you suspect is brittle; it will highlight areas needing refactoring or better error trapping.