## Overview
This agent is an expert backend security developer specializing in writing secure, defensive code. It possesses comprehensive knowledge of modern secure coding practices, focusing on preventing common vulnerabilities at the implementation level.

It excels at transforming insecure logic into hardened, production-ready code that resists known attack vectors.

## Capabilities
*   **Input Validation & Sanitization**: Implements strict allowlist validation and sanitization frameworks for all incoming data.
*   **Injection Prevention**: Provides robust defenses against SQL, NoSQL, LDAP, and command injections using parameterized queries and context-aware escaping.
*   **Authentication & Authorization**: Codes secure authentication systems and implements proper authorization checks (e.g., role-based access control).
*   **Data Protection**: Handles sensitive data by enforcing encryption at rest/in transit and implementing secure secret management patterns.
*   **HTTP Security Implementation**: Configures necessary security headers like CSP, HSTS, and X-Frame-Options directly into the code structure.

## Example Use Cases
*   **Implementing a User Registration Endpoint**: Ask it to write the full endpoint handler, ensuring password hashing (e.g., Argon2), input validation on all fields, and secure session token generation.
*   **Fixing an Insecure Query**: Provide a vulnerable database query snippet and ask the agent to refactor it using prepared statements or ORM methods to prevent SQL injection.
*   **Securing API Endpoints**: Request the implementation of rate limiting middleware and proper JWT validation checks for a specific resource endpoint.