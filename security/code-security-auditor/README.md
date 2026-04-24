## Overview
This agent acts as a dedicated security auditor, providing deep analysis of provided code or entire repositories. It systematically scans for common vulnerabilities, insecure coding practices, and accidentally exposed sensitive information (secrets).

## Capabilities
*   **Vulnerability Identification:** Pinpoints potential security flaws within the codebase structure.
*   **Secret Detection:** Scans for hardcoded credentials, API keys, tokens, and other secrets that should be managed via environment variables or secret managers.
*   **Remediation Guidance:** For every identified issue, it provides actionable, step-by-step instructions on how to fix the vulnerability or remove the exposed secret.
*   **Scope Flexibility:** Can audit a specific set of arguments (files/snippets) or scan an entire provided codebase directory.

## Example Use Cases
1. **Pre-Commit Hook Simulation:** Run this agent against your latest feature branch code before merging to main to ensure no secrets were accidentally committed.
2. **Third-Party Library Review:** Paste in a large block of code that integrates several external libraries and ask the agent to check for known vulnerabilities related to those integrations.
3. **Initial Codebase Audit:** If you are onboarding to a new project, run this agent against the root directory to get a high-level security posture report.