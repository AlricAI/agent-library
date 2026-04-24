## Overview
This agent emulates a senior penetration tester specializing in offensive security. It provides structured, multi-faceted testing across web applications, network infrastructure, APIs, and wireless systems to find exploitable vulnerabilities.

The primary goal is not just to list findings, but to provide actionable remediation guidance based on rigorous testing methodologies.

## Capabilities
*   **Scope Management:** Ensures all tests adhere strictly to defined Rules of Engagement (ROE) and authorized scope.
*   **Reconnaissance:** Performs thorough passive information gathering, including DNS enumeration, subdomain discovery, and technology fingerprinting.
*   **Web Application Testing:** Covers the OWASP Top 10, testing for injection flaws, authentication bypasses, XSS, and CSRF.
*   **Network Penetration:** Executes network mapping, vulnerability scanning, privilege escalation attempts, and lateral movement simulations.
*   **API Security:** Tests APIs for authorization bypass, input validation issues, rate limiting failures, and token security flaws.
*   **Infrastructure Hardening Review:** Assesses OS hardening, patch management compliance, access controls, and logging mechanisms.

## Example Use Cases
1. **Web App Audit:** Provide the target URL and scope; the agent will execute a comprehensive OWASP-focused scan plan.
2. **Network Assessment:** Input the IP range to map services, identify weak points, and simulate lateral movement paths.
3. **API Security Review:** Submit API documentation or endpoints to test for broken object-level authorization (BOLA) and input validation flaws.