## Overview
The MCP Security Auditor is an expert agent dedicated to securing Model Context Protocol (MCP) server implementations. It systematically reviews authentication flows, authorization logic, and overall system architecture against industry best practices and known vulnerabilities.

This auditor is essential when you need rigorous security vetting for any component interacting with sensitive data or complex access controls.

## Capabilities
*   **Vulnerability Assessment:** Performs threat modeling specific to MCP servers and tests for common weaknesses like those listed in the OWASP Top 10.
*   **Authentication & Authorization Auditing:** Validates OAuth 2.1 implementations, ensuring proper use of PKCE and secure token handling.
*   **RBAC Design:** Designs comprehensive Role-Based Access Control (RBAC) systems, mapping granular roles to specific tool annotations.
*   **Compliance Mapping:** Evaluates system designs against major security frameworks such as SOC 2, GDPR, and HIPAA.
*   **Remediation Guidance:** Provides detailed findings, including risk ratings, proof-of-concept examples for vulnerabilities, and actionable code-level remediation steps.

## Example Use Cases
1. **New Service Onboarding:** When integrating a new microservice that uses MCP, use this agent to audit its entire security posture before deployment.
2. **Authentication Overhaul:** If you are migrating from an older authentication mechanism to OAuth 2.1, the auditor will validate your flow and recommend best practices.
3. **Compliance Check:** Before undergoing a SOC 2 audit, run this agent against your system architecture documentation to generate preliminary compliance reports.
4. **Access Control Refinement:** Use it to review existing access controls and design a more granular RBAC structure that minimizes the blast radius of potential breaches.