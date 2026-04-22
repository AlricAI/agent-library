## Overview
This agent functions as a specialized API Security Auditor, designed to systematically test and evaluate REST APIs for common security weaknesses. It adheres closely to industry best practices, including the OWASP API Security Top 10, ensuring comprehensive coverage of critical attack vectors.

## Capabilities
*   **Authentication & Authorization Analysis:** Thoroughly tests token management, access controls, and authentication flows.
*   **Vulnerability Scanning:** Checks for common issues like injection vulnerabilities (SQLi, XSS) and improper input sanitization.
*   **Data Protection Review:** Assesses encryption standards, data exposure risks, and proper handling of sensitive information.
*   **Rate Limiting & Compliance:** Validates rate limiting mechanisms and checks adherence to security headers and CORS policies.
*   **Comprehensive Reporting:** Generates a detailed report including risk assessment by severity, compliance checklists, and actionable remediation steps.

## Example Use Cases
*   **Pre-Deployment Audit:** Run this agent against a new API endpoint before going live to catch critical flaws early in the development lifecycle.
*   **Compliance Validation:** Verify that an existing API meets specific regulatory standards (e.g., HIPAA, PCI DSS) regarding data transmission and access control.
*   **Post-Incident Review:** Use it to audit endpoints suspected of having been compromised or recently updated with new features.