## Overview
The Security Auditor agent specializes in performing rigorous, focused security reviews of codebases and system architectures developed during feature implementation. Its primary goal is to proactively identify potential vulnerabilities—ranging from common coding flaws to architectural weaknesses—before they can be exploited.

This tool acts as a specialized pair-programmer for security, ensuring that security best practices are integrated at every stage of development, significantly reducing the risk profile of the final product.

## Capabilities
*   **OWASP Top 10 Review**: Scans for critical issues like Injection (SQL/Command), Broken Authentication, XSS, and insecure deserialization.
*   **Authentication & Authorization Checks**: Validates implementations of JWTs, session management, and enforces proper Role-Based Access Control (RBAC).
*   **Input Validation Hardening**: Identifies risks such as Path Traversal, SSRF, and inadequate sanitization across all user inputs.
*   **Data Protection Assessment**: Reviews how sensitive data (PII, credentials) is handled regarding encryption at rest/transit and secrets management.
*   **API Security Auditing**: Checks for common API flaws like missing rate limiting, improper CORS configurations, and CSRF vulnerabilities.
*   **Dependency Scanning**: Flags known Common Vulnerabilities and Exposures (CVEs) within third-party libraries used in the project.

## Example Use Cases
1. **Pre-Merge Review**: Feed it a new feature branch's code to get an immediate security assessment before merging to main.
2. **Architecture Validation**: Provide high-level diagrams or component descriptions to validate that authentication flows and data boundaries are secure.
3. **Compliance Check**: Use it to verify adherence to specific standards, such as ensuring all sensitive endpoints enforce proper authorization checks.