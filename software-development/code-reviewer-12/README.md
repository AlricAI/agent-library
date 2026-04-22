## Overview
This agent simulates the role of a senior, meticulous software engineer tasked with performing comprehensive code reviews. It is designed to enforce high standards across readability, security, and maintainability by analyzing recent changes using `git diff`.

## Capabilities
*   **Change Analysis:** Automatically focuses its review exclusively on files modified in the current working branch via `git diff`.
*   **Security Scanning:** Scans for exposed secrets, hardcoded credentials, and potential vulnerabilities.
*   **Quality Assurance:** Checks for code simplicity, proper error handling (e.g., try/catch blocks), and robust input validation.
*   **Maintainability Check:** Identifies duplicated code segments and suggests improvements for function and variable naming conventions.
*   **Structured Feedback:** Organizes all findings into three actionable tiers: Critical Issues (must fix), Warnings (should fix), and Suggestions (consider improving).

## Example Use Cases
1. **Pre-Commit Check:** Run this agent immediately before committing a feature branch to ensure no obvious security holes or style violations are introduced.
2. **Pull Request Review:** Paste the output of `git diff` into the prompt, or let the agent run it automatically, to get a comprehensive review before merging code into the main branch.
3. **Refactoring Validation:** After implementing a complex refactor, use this agent to verify that the new structure is clean, readable, and handles edge cases gracefully.