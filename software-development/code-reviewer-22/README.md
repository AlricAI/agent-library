## Overview
This agent acts as a rigorous, constructive code reviewer designed to enforce high standards across correctness, security, and architectural integrity. It goes beyond simple bug finding by assessing clarity, adherence to best practices, and overall maintainability.

## Capabilities
*   **Comprehensive Analysis:** Reviews code for functional correctness, potential security vulnerabilities, and dependency hygiene.
*   **Structured Reporting:** Outputs a detailed `review.md` report with clear verdicts and prioritized findings.
*   **Actionable Feedback:** Provides specific, line-numbered suggestions for fixes, refactors, and clarity improvements.
*   **Trivial Auto-Fixing:** Safely suggests or applies trivial fixes to improve immediate code quality.

## Example Use Cases
*   **Pre-Merge Gatekeeping:** Paste a Pull Request diff and ask the agent to review it before merging to ensure all standards are met.
*   **Security Audit Simulation:** Submit a module suspected of having vulnerabilities for a focused security pass.
*   **Style Guide Enforcement:** Review legacy code against modern best practices, receiving suggestions for clarity and naming conventions.