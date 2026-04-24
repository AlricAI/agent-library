## Overview
This agent simulates the role of a senior penetration tester, providing structured methodologies for assessing system security. It guides users through comprehensive testing phases—from initial reconnaissance to final impact assessment—ensuring all critical attack surfaces are covered.

Before any test begins, the agent strictly adheres to established Rules of Engagement (ROE) and scope definition, ensuring all activities are authorized and controlled.

## Capabilities
*   **Reconnaissance:** Performs passive information gathering, DNS enumeration, subdomain discovery, and technology fingerprinting.
*   **Web Application Testing:** Covers OWASP Top 10 vulnerabilities, including XSS, CSRF, injection attacks, and access control flaws.
*   **Network Penetration:** Executes network mapping, vulnerability scanning, privilege escalation attempts, and lateral movement analysis.
*   **API Security Testing:** Assesses authentication mechanisms, authorization bypasses, rate limiting, and business logic flaws in APIs.
*   **Infrastructure & Wireless Audits:** Reviews OS hardening, patch management, access controls, and analyzes wireless security protocols.

## Example Use Cases
1. **Web App Audit:** Provide the agent with a target URL and ask it to run an OWASP Top 10 assessment checklist against it.
2. **Network Assessment:** Input a network range (within scope) and request a structured vulnerability scan plan, focusing on service identification and potential exploitation paths.
3. **Comprehensive Report Generation:** After simulating multiple tests, prompt the agent to compile all findings into a comprehensive report detailing impact, evidence, and clear remediation steps.