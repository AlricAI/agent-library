## Overview
The MCP Security Auditor is an expert agent designed to conduct comprehensive security reviews for Model Context Protocol (MCP) server implementations. It specializes in hardening authentication, designing granular Role-Based Access Control (RBAC), and ensuring adherence to major compliance frameworks like SOC 2, GDPR, and HIPAA.

This auditor systematically assesses the entire security posture of an MCP system, moving beyond simple vulnerability scanning to provide actionable architectural recommendations.

## Capabilities
*   **Systematic Security Assessment:** Conducts deep dives into authentication flows and authorization logic for MCP servers.
*   **Threat Modeling:** Performs threat modeling tailored specifically to protocol vulnerabilities within the MCP ecosystem.
*   **OAuth 2.1 Validation:** Validates implementations, paying close attention to best practices like Proof Key for Code Exchange (PKCE) and secure token handling.
*   **RBAC Design & Implementation:** Designs comprehensive RBAC models, mapping specific roles directly to tool annotations and permissions.
*   **Vulnerability Testing:** Tests for common flaws, including those listed in the OWASP Top 10, alongside MCP-specific attack vectors.
*   **Compliance Mapping:** Evaluates current implementations against established security frameworks, providing clear compliance gaps.

## Example Use Cases
*   **New System Onboarding:** When integrating a new service using an MCP backend, use this agent to generate an initial risk assessment and required security hardening checklist.
*   **Authentication Overhaul:** If migrating from basic API keys to OAuth 2.1, utilize the auditor to validate the entire token lifecycle and flow implementation.
*   **Compliance Audit Prep:** Before undergoing a SOC 2 audit, run this agent against your current architecture to receive a gap analysis report mapped directly to required controls.
*   **High-Risk Feature Deployment:** When deploying any feature that involves destructive actions or elevated privileges, use the auditor to design and validate the necessary granular RBAC policies.