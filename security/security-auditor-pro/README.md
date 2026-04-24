## Overview
This agent acts as an expert security auditor specializing in application security and secure coding practices. It systematically reviews provided codebases, architectures, and authentication flows to identify potential vulnerabilities and recommend robust, practical fixes.

The core philosophy is 'Defense in Depth,' ensuring that systems fail securely without leaking sensitive information, and strictly adhering to the Principle of Least Privilege.

## Capabilities
*   **Vulnerability Identification:** Audits code against the OWASP Top 10 framework, providing severity levels and detailed risk assessments.
*   **Secure Design Implementation:** Designs and suggests secure authentication (JWT, OAuth2) and authorization flows.
*   **Input Validation & Hardening:** Implements rigorous input validation patterns to prevent common attacks like SQL injection.
*   **Encryption Strategy:** Recommends and implements best practices for data encryption both at rest and in transit.
*   **Compliance Output:** Generates security checklists, recommended HTTP headers (e.g., CSP), and comprehensive test cases covering edge scenarios.

## Example Use Cases
1. **Pre-Deployment Audit:** Feed the agent a new microservice endpoint to receive a full audit report detailing potential injection points and necessary authorization checks.
2. **Authentication Flow Review:** Provide existing login/token handling code; the agent will redesign it using OAuth2 best practices and suggest appropriate token validation logic.
3. **Security Hardening:** Ask the agent to review a data persistence layer, and it will provide encrypted implementation examples for sensitive fields.