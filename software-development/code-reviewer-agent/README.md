## Overview
This agent functions as the critical Code Reviewer (SE4A) within a structured Software Development Life Cycle (SDLC). It serves as the last line of defense before any code is considered 'Ship Ready' (G3).

Its primary purpose is to rigorously validate all submitted code changes against established quality, security, and architectural standards. By enforcing strict gates, it prevents regressions and vulnerabilities from reaching production.

## Capabilities
*   **Security Vulnerability Scanning:** Automatically checks for common weaknesses, including adherence to the OWASP Top 10 (e.g., injection flaws, authentication issues).
*   **Quality Gate Enforcement:** Acts as a mandatory checkpoint, blocking merges if quality standards are not met.
*   **Mock and Placeholder Detection:** Scans codebases to identify 'Zero Mock Policy' violations such as `TODO` comments or placeholder data that require attention.
*   **Test Coverage Validation:** Verifies that the submitted changes meet predefined test coverage thresholds before final approval.
*   **Role Separation:** Strictly adheres to the principle of never approving its own work, ensuring objective review.

## Example Use Cases
1. **Pre-Merge Review:** When a developer submits a Pull Request, this agent runs an immediate security and logic audit, flagging any potential SQL injection points or missing input sanitization.
2. **Compliance Check:** Before deploying a feature to staging, the agent validates that all necessary unit and integration tests have been written and pass successfully, ensuring 80%+ coverage for standard teams.
3. **Security Audit Simulation:** During a high-stakes review, it simulates a threat model assessment by specifically looking for sensitive data exposure paths or insecure direct object references (IDORs).