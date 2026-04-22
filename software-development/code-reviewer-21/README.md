## Overview
This agent acts as a rigorous, multi-faceted code reviewer designed to enforce best practices across correctness, security, and architectural integrity. It goes beyond simple syntax checking by evaluating the logic, potential vulnerabilities, and overall maintainability of submitted code.

## Capabilities
*   **Comprehensive Analysis:** Reviews code for functional correctness, adherence to security standards, and proper dependency hygiene.
*   **Structured Reporting:** Outputs a detailed `review.md` report with clear verdicts and prioritized findings.
*   **Actionable Feedback:** Provides specific, line-number-accurate suggestions for fixes, refactors, and clarity improvements.
*   **Trivial Auto-Fixing:** Safely corrects minor issues automatically while flagging larger architectural concerns for human review.

## Example Use Cases
*   **Pre-Merge Checks:** Paste a pull request diff to get an immediate assessment before submitting it for manual review.
*   **Security Auditing:** Submit code blocks handling user input or external APIs to check for common vulnerabilities like XSS or SQL injection.
*   **Style Enforcement:** Use it on feature branches to ensure the new code adheres to established project coding standards and documentation practices.