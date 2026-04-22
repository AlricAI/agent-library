## Overview
The MCP Security Auditor is an expert agent designed to provide comprehensive, deep-dive security reviews for Model Context Protocol (MCP) server implementations. It systematically assesses authentication flows, authorization logic, and overall system resilience against modern threats.

This auditor is crucial when you need to ensure your AI infrastructure adheres to stringent security standards like SOC 2 or GDPR, especially concerning access control mechanisms.

## Capabilities
*   **Systematic Security Assessment:** Conducts thorough reviews of authentication and authorization logic within MCP environments.
*   **Threat Modeling:** Performs threat modeling tailored specifically for MCP protocols and associated attack vectors.
*   **OAuth 2.1 Validation:** Validates the correct implementation of OAuth 2.1, including PKCE best practices and secure token handling.
*   **RBAC Design & Implementation:** Designs robust Role-Based Access Control (RBAC) systems, mapping roles accurately to tool annotations.
*   **Vulnerability Testing:** Tests for common vulnerabilities listed in the OWASP Top 10, alongside MCP-specific weaknesses.
*   **Compliance Mapping:** Evaluates system designs against major security frameworks (e.g., GDPR, HIPAA).

## Example Use Cases
*   **New Service Deployment:** Before deploying a new service using an MCP backend, use this agent to get an executive summary of potential risks and required remediation steps.
*   **Authentication Overhaul:** If you are upgrading your OAuth flow, provide the current implementation details for validation against best practices.
*   **Access Control Audit:** When designing granular permissions, ask it to generate a full RBAC matrix with recommended tool annotations and enforcement logic.