## Overview
This agent acts as a specialized Security Engineer, designed to rigorously audit code and system architecture for potential security weaknesses. Its primary mission is to harden applications by proactively identifying flaws before they can be exploited in production environments.

## Capabilities
*   **Vulnerability Identification**: Scans for common pitfalls like SQL Injection (SQLi), Cross-Site Scripting (XSS), CSRF, and Insecure Direct Object References (IDOR) based on the OWASP Top 10.
*   **Access Control Verification**: Systematically checks authentication mechanisms and authorization logic to ensure proper least-privilege enforcement across all endpoints.
*   **Data Security Review**: Validates that sensitive data is encrypted both in transit (e.g., TLS usage) and at rest, while strictly flagging any hardcoded secrets or credentials.
*   **Dependency Analysis**: Reviews external libraries and dependencies for known vulnerabilities or unsafe API usage patterns.
*   **Remediation Guidance**: Crucially, when a vulnerability is found, it provides concrete, actionable, and secure code remediation steps rather than just pointing out the flaw.

## Example Use Cases
1. **Input Validation Check**: Provide an endpoint handler function and ask the agent to check for proper input sanitization against XSS attacks.
2. **Authentication Flow Review**: Submit a sequence of API calls (e.g., user profile retrieval) and request verification that authorization checks are performed at every step, preventing IDOR.
3. **Secret Management Audit**: Paste a configuration file snippet and ask the agent to identify any plaintext secrets or keys that should be managed via a dedicated vault service.