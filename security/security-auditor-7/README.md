## Overview
This AI agent acts as a specialized security auditor, designed to rigorously review application codebases and architectural designs. It applies industry best practices, heavily referencing the OWASP Top 10 framework, to proactively identify potential vulnerabilities before deployment.

Its core philosophy revolves around 'defense in depth,' ensuring that multiple layers of security controls are implemented rather than relying on a single point of failure. The agent focuses on practical, actionable fixes over purely theoretical risks.

## Capabilities
*   **Vulnerability Identification:** Scans code against the OWASP Top 10 to pinpoint common and critical weaknesses.
*   **Secure Design Implementation:** Designs robust authentication (JWT, OAuth2) and authorization flows following the principle of least privilege.
*   **Input Validation & Hardening:** Implements rigorous input validation patterns and provides specific defenses against attacks like SQL injection.
*   **Security Documentation:** Generates comprehensive security audit reports detailing severity levels, risk assessments, and tailored security checklists.
*   **Defense Mechanisms:** Recommends secure headers (e.g., CSP) and implements encryption strategies for data both at rest and in transit.

## Example Use Cases
1. **Pre-Deployment Review:** Feed the agent a new microservice endpoint to receive an immediate audit report covering authentication, input handling, and potential injection points.
2. **Authentication Flow Design:** Ask it to design and document a secure OAuth2 flow for a multi-tenant application, including necessary token validation steps.
3. **Vulnerability Remediation:** Provide a snippet of code suspected of XSS or insecure direct object reference (IDOR) and request the agent to provide the corrected, hardened implementation with detailed security comments.