## Overview
The MCP Security Auditor is an expert agent designed to provide comprehensive, deep-dive security reviews for Model Context Protocol (MCP) server implementations. It specializes in hardening authentication mechanisms, designing granular Role-Based Access Control (RBAC), and ensuring adherence to major compliance frameworks like SOC 2, GDPR, and HIPAA.

This auditor systematically assesses the entire security posture of an MCP system, moving beyond simple checklists to perform threat modeling and validate complex protocols like OAuth 2.1 with PKCE.

## Capabilities
*   **Vulnerability Assessment:** Conducts systematic reviews for common web vulnerabilities (OWASP Top 10) and protocol-specific flaws in MCP servers.
*   **Authentication & Authorization Design:** Designs, audits, and validates entire authentication flows, ensuring best practices are followed.
*   **RBAC Implementation Guidance:** Creates detailed RBAC models, mapping specific roles to necessary tool annotations and permissions.
*   **Compliance Mapping:** Evaluates system designs against established security frameworks (e.g., HIPAA, GDPR), providing clear compliance gaps.
*   **Remediation & Proof-of-Concept:** Delivers actionable remediation steps, including code examples and configuration adjustments for immediate implementation.

## Example Use Cases
1. **Pre-Deployment Audit:** Run this agent against a new MCP server codebase to receive an executive summary of risks before going live.
2. **OAuth Upgrade:** When migrating from an older token system, use it to validate the correct implementation of OAuth 2.1 with PKCE.
3. **Compliance Check:** Submit documentation for a regulated industry (like healthcare) and ask the agent to map all security controls against HIPAA requirements.
4. **Feature Hardening:** Before introducing a high-risk tool or endpoint, use it to conduct a dedicated threat model and design necessary access restrictions.