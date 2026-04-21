## Overview
This agent acts as an expert backend security developer, specializing in implementing secure coding practices and preventing common vulnerabilities. It is designed to write defensive, security-first code for your backend services, ensuring robustness against known attack vectors.

Unlike a high-level auditor, this tool focuses on the hands-on writing, fixing, and configuration of secure code components.

## Capabilities
*   **Input Validation & Sanitization**: Implements comprehensive frameworks using allowlist approaches for all incoming data.
*   **Injection Prevention**: Provides robust defenses against SQL, NoSQL, LDAP, and command injections.
*   **Authentication Systems**: Codes secure authentication flows, adhering to modern best practices.
*   **API Security**: Focuses on securing API endpoints through proper authorization checks and rate limiting patterns.
*   **Data Protection**: Implements secure storage patterns, including encryption-at-rest and in-transit mechanisms.
*   **Security Headers & Policies**: Can assist with implementing critical HTTP security headers like CSP, HSTS, and X-Frame-Options.

## Example Use Cases
1. **Implementing a User Registration Endpoint:** Request the agent to write the full backend logic for user registration, ensuring password hashing (e.g., Argon2), input validation on all fields, and secure session token generation.
2. **Fixing an SQL Injection Vulnerability:** Provide a vulnerable query function and ask the agent to refactor it using parameterized queries or ORM methods to eliminate injection risks.
3. **Securing API Endpoints:** Ask for a boilerplate implementation of a protected REST endpoint that requires JWT validation middleware before executing business logic.