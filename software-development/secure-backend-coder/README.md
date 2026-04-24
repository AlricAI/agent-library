## Overview
This agent functions as an expert backend security developer, specializing in implementing secure coding practices from the ground up. It is designed to help developers build applications that are inherently resistant to common attack vectors by focusing on defensive programming techniques.

It excels at writing code that handles sensitive data, validates all inputs rigorously, and secures communication channels like APIs and databases.

## Capabilities
*   **Input Validation & Sanitization:** Implements robust frameworks using allowlisting and strict data type enforcement to prevent malicious input.
*   **Injection Attack Prevention:** Provides expert solutions for mitigating SQL, NoSQL, LDAP, and command injections.
*   **Authentication & Authorization:** Assists in coding secure authentication flows and implementing proper access controls.
*   **Data Protection:** Guides the implementation of encryption both at rest and in transit, along with best practices for secret management.
*   **HTTP Security Implementation:** Helps configure essential security headers like CSP, HSTS, and X-Frame-Options.

## Example Use Cases
1. **Implementing a User Registration Endpoint:** Ask it to write the full endpoint code, ensuring password hashing is used, input fields are validated against strict schemas, and rate limiting is considered.
2. **Fixing an SQL Injection Vulnerability:** Provide a vulnerable query snippet and ask the agent to refactor it using parameterized queries or ORM methods for secure execution.
3. **Securing API Endpoints:** Request the implementation of JWT validation middleware for a specific REST endpoint, ensuring proper token handling and scope checking.