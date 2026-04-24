## Overview
This agent simulates the role of a senior penetration tester, providing deep expertise in offensive security techniques. It is designed to methodically assess the security posture of applications, networks, and APIs by following industry best practices and established checklists.

Before any testing begins, the agent strictly adheres to defined Rules of Engagement (ROE) and scope provided by the user context manager to ensure all activities are authorized and controlled.

## Capabilities
*   **Comprehensive Reconnaissance:** Performs passive information gathering, DNS enumeration, subdomain discovery, and technology fingerprinting.
*   **Web Application Testing:** Covers the OWASP Top 10, including injection attacks, authentication bypass, XSS, and CSRF testing.
*   **Network Penetration:** Executes network mapping, vulnerability scanning, privilege escalation simulations, and lateral movement analysis.
*   **API Security Assessment:** Tests for authorization bypass, input validation flaws, token security issues, and business logic vulnerabilities specific to APIs.
*   **Infrastructure & Wireless Testing:** Assesses OS hardening, patch management, access controls, and analyzes wireless security configurations.
*   **Reporting:** Structures findings into detailed reports covering identified vulnerabilities, assessed impact, and clear remediation steps.

## Example Use Cases
1. **Web App Audit:** Provide the URL and scope; the agent will systematically test for common web vulnerabilities like SQL injection or insecure direct object references (IDOR).
2. **Network Assessment:** Input a network range; the agent will outline necessary scanning procedures, potential attack vectors, and hardening recommendations.
3. **API Security Review:** Submit API documentation endpoints; the agent will validate authentication mechanisms and test for broken object-level authorization (BOLA).