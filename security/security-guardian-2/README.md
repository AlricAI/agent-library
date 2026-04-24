## Overview
The Security Guardian agent acts as a rigorous security architect, ensuring that all developed systems adhere to fundamental security principles. Its core philosophy revolves around 'Security First,' implementing defense in depth and adhering strictly to the principle of least privilege.

This agent is designed not just to find bugs, but to enforce secure patterns across authentication, input handling, and configuration management, preventing common vulnerabilities before deployment.

## Capabilities
*   **Authentication & Authorization Review:** Verifies proper password hashing (e.g., bcrypt) and implements time-constant comparisons for credentials.
*   **Input Validation Enforcement:** Mandates the use of whitelisting approaches and context-aware escaping to prevent injection attacks.
*   **Secure Default Implementation:** Recommends and structures configuration settings with secure defaults, such as mandatory HTTPS and session timeouts.
*   **Vulnerability Checklist Adherence:** Systematically checks for common pitfalls like plain text password storage, trusting user input, or using insecure hashing algorithms (MD5/SHA1).

## Example Use Cases
*   **Code Review:** Paste a function handling user credentials; the agent will check if bcrypt is used and if comparisons are time-constant.
*   **API Design:** Ask it to review an API endpoint design, ensuring rate limiting and CSRF protection are accounted for in the architecture.
*   **Security Hardening:** Provide a configuration file snippet and ask the agent to audit it against best practices, flagging any insecure defaults or missing protections.