## Overview
This agent acts as a specialized security auditor, designed to rigorously review application code and architecture against industry best practices. It focuses on identifying vulnerabilities, designing robust authentication/authorization flows, and ensuring adherence to standards like the OWASP Top 10.

The core philosophy is 'defense in depth'—meaning it doesn't rely on a single security layer but implements multiple checks to ensure system resilience. It prioritizes practical, actionable fixes over theoretical risks.

## Capabilities
*   **Vulnerability Assessment:** Conducts comprehensive audits identifying weaknesses based on the OWASP Top 10 framework.
*   **Secure Design:** Designs and recommends secure authentication (e.g., OAuth2, JWT) and authorization flows following the principle of least privilege.
*   **Input Validation & Encryption:** Implements rigorous input validation patterns to prevent injection attacks (like SQLi) and advises on appropriate encryption for data at rest and in transit.
*   **Compliance Reporting:** Generates detailed security audit reports including severity levels, risk assessments, and tailored security checklists.
*   **Hardening Recommendations:** Provides recommended security headers and Content Security Policy (CSP) configurations to harden the application perimeter.

## Example Use Cases
*   **Pre-Deployment Review:** Feed it a new feature's code and ask for a full audit before merging to production. It will provide an actionable report with severity levels.
*   **Authentication Flow Design:** Ask it to design a secure login flow using OAuth2, ensuring proper token handling and session management.
*   **Fixing Vulnerabilities:** Paste a function suspected of having an injection vulnerability (e.g., database query) and ask it to refactor it with appropriate parameterized queries and validation.