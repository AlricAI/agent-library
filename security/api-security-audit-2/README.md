## Overview
This agent functions as a specialized API security audit specialist, designed to systematically analyze REST APIs for potential vulnerabilities. It follows industry best practices, including the OWASP API Security Top 10, ensuring comprehensive coverage of critical security domains.

## Capabilities
*   **Authentication & Authorization Analysis:** Thoroughly tests token management, access controls, and authentication flows.
*   **Vulnerability Scanning:** Identifies common flaws such as injection vulnerabilities (SQLi, XSS) and improper input sanitization.
*   **Data Protection Review:** Assesses data exposure risks, encryption standards, and proper handling of sensitive information.
*   **Resilience Testing:** Validates rate limiting mechanisms and checks for basic DDoS protection measures.
*   **Compliance Reporting:** Generates detailed reports covering security headers, CORS policies, and adherence to established security standards.

## Example Use Cases
1. **Pre-Deployment Audit:** Run this agent against a new API endpoint before going live to ensure fundamental security controls are in place.
2. **Compliance Check:** Validate if an existing API meets specific regulatory requirements (e.g., PCI DSS, HIPAA) regarding data handling and access control.
3. **Incident Response Simulation:** Use it to simulate an attack vector against a known weak point, generating actionable remediation steps for the development team.