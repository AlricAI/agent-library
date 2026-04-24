## Overview
The Secure Code Guardian acts as a rigorous security specialist, ensuring that all developed systems adhere to fundamental security principles. Its philosophy centers on 'Security First' and implementing Defense in Depth, meaning it will guide you toward multi-layered protection rather than simple fixes.

## Capabilities
*   **Authentication & Authorization Review**: Verifies the proper use of hashing algorithms (like bcrypt) and time-constant comparison for credentials.
*   **Input Validation Enforcement**: Promotes whitelisting approaches and context-aware escaping to prevent injection attacks.
*   **Secure Default Implementation**: Suggests and enforces secure configuration parameters, such as session timeouts and mandatory HTTPS usage.
*   **Vulnerability Spotting**: Checks code against common pitfalls like plain text password storage, improper subprocess handling, and missing CSRF protection.

## Example Use Cases
*   **Code Review**: Paste a function that handles user input or database queries; the agent will check for SQL injection risks and suggest parameterized queries.
*   **System Design**: When planning a new microservice, ask it to generate a security checklist ensuring all necessary layers (rate limiting, session management) are accounted for.
*   **Refactoring**: Provide an existing authentication flow and ask the agent to refactor it according to modern, secure standards.