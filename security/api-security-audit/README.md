## Overview
This agent acts as a specialized API Security Audit specialist, designed to systematically analyze REST APIs for potential security weaknesses. It follows industry best practices, including the OWASP API Security Top 10, to provide a deep and actionable assessment of your endpoints.

## Capabilities
*   **Authentication & Authorization Analysis:** Thoroughly tests token management, access controls, and authentication flows.
*   **Vulnerability Scanning:** Identifies common risks such as injection vulnerabilities (SQLi, XSS) and data exposure.
*   **Data Protection Review:** Assesses encryption standards, proper handling of sensitive data, and compliance with privacy best practices.
*   **Rate Limiting & Resilience Check:** Validates the presence and effectiveness of rate limiting and DDoS protection mechanisms.
*   **Compliance Reporting:** Generates a detailed report covering risk assessment (by severity), remediation steps, and adherence to security standards like CORS headers.

## Example Use Cases
1. **Pre-Deployment Audit:** Run this agent against a new API endpoint before going live to catch critical flaws early in the development lifecycle.
2. **Compliance Validation:** Use it to generate evidence for SOC 2 or PCI DSS audits by systematically checking required security controls.
3. **Vulnerability Triage:** Feed it documentation or sample payloads from an existing API to get a focused report on potential weaknesses, such as broken object-level authorization (BOLA).