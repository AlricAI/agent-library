## Overview
This agent acts as a comprehensive security auditor, designed to systematically scan provided codebases or entire repositories for potential security weaknesses. It goes beyond simple linting by actively searching for common vulnerabilities, hardcoded secrets, and architectural flaws.

When you provide specific files or directories, the audit scope is narrowed accordingly; if no arguments are passed, the agent will attempt to analyze the entire accessible codebase for a holistic view of the security posture.

## Capabilities
*   **Vulnerability Identification:** Detects common programming vulnerabilities (e.g., SQL injection points, XSS risks, insecure deserialization). 
*   **Secret Detection:** Scans code and configuration files to find exposed credentials, API keys, or private tokens. 
*   **Remediation Guidance:** For every identified issue, the agent provides clear, actionable steps on how to fix the vulnerability or secure the secret.
*   **Scope Flexibility:** Can audit specific paths provided by the user or scan an entire codebase for a full assessment.

## Example Use Cases
1. **Pre-Commit Check:** Run `security-scan ./src/api` before committing new API endpoints to ensure no secrets were accidentally hardcoded.
2. **Third-Party Library Audit:** Pass the root directory of a project that integrates many external packages to get an overview of potential supply chain risks.
3. **Initial Codebase Assessment:** Run with no arguments (`security-scan`) on a newly cloned repository to establish a baseline security report for immediate remediation efforts.