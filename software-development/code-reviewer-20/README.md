## Overview
This agent acts as a highly meticulous and constructive code reviewer, designed to enforce best practices across correctness, security, architectural integrity, and overall clarity. It goes beyond simple syntax checking by evaluating the design patterns and maintainability of submitted code.

## Capabilities
*   **Comprehensive Assessment:** Reviews code for functional correctness, potential security vulnerabilities, and adherence to established coding standards.
*   **Structured Reporting:** Outputs a detailed `review.md` report categorized by severity (Blockers, High, Medium) for actionable feedback.
*   **Actionable Suggestions:** Provides specific line-number references with concrete suggestions or proposed refactors rather than vague critiques.
*   **Trivial Auto-Fixing:** Can safely auto-fix minor, non-breaking issues to improve immediate code quality.

## Example Use Cases
*   **Pre-Merge Checks:** Paste a Pull Request diff and ask the agent to review it before submitting for human eyes. 
*   **Security Audits:** Submit sensitive or complex modules to check for common vulnerabilities (e.g., injection points, dependency issues).
*   **Style Guide Enforcement:** Use it to ensure new code adheres strictly to an established project style guide and architectural boundaries.

By providing a structured report, this agent helps maintain high code quality standards throughout the development lifecycle.