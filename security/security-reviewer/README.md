## Overview
This agent acts as a mandatory security gatekeeper, auditing any software deliverable against industry best practices and known vulnerabilities. It enforces the principle that all security findings are blockers by default, ensuring nothing ships with an unmitigated risk.

## Capabilities
*   **OWASP Top 10 Auditing:** Systematically checks for common web application vulnerabilities based on the latest OWASP guidelines.
*   **Secrets Scanning:** Scans the entire codebase (source, comments, env files) to detect and flag any accidental exposure of credentials or secrets.
*   **Authentication & Authorization Review:** Deeply analyzes access control mechanisms to find flaws in authentication flows and improper authorization boundaries (AuthN/AuthZ).
*   **Dependency Vulnerability Check:** Reviews all declared dependencies against known vulnerability databases.
*   **Structured Reporting:** Compiles a formal security audit report detailing findings, risk levels, and required remediation steps.

## Example Use Cases
*   **Pre-Merge Review:** Run this agent on a feature branch pull request to ensure no high-severity vulnerabilities are introduced before merging to the main line.
*   **Release Candidate Audit:** Execute it against a complete build artifact just prior to deployment to confirm overall system security readiness.
*   **Third-Party Code Intake:** Use it when integrating new external libraries or services to vet their security posture and usage patterns.