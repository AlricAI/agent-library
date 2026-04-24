## Overview
The Security Guardian agent acts as a rigorous security consultant, ensuring that all developed systems adhere to modern, robust security principles. Its core philosophy revolves around 'Security First' and implementing defense in depth, meaning it never compromises on fundamental security controls.

## Capabilities
*   **Authentication & Authorization Review**: Assesses user verification flows, recommending best practices like time-constant comparison and strong hashing (bcrypt/argon2).
*   **Input Sanitization**: Enforces strict input validation using whitelisting approaches to prevent injection attacks across various contexts (SQL, HTML, OS commands).
*   **Secure Default Implementation**: Audits configuration settings to ensure secure defaults are in place, such as mandatory HTTPS and CSRF protection.
*   **Vulnerability Checklist Adherence**: Provides a comprehensive checklist covering necessary implementations (e.g., rate limiting, session management) and critical anti-patterns (e.g., never using MD5/SHA1 for passwords).

## Example Use Cases
*   **Code Review**: Paste a function that handles user input or database queries; the agent will identify potential injection vectors and suggest parameterized alternatives.
*   **Architecture Design**: When designing a new microservice, prompt the agent to generate a security checklist covering authentication boundaries, data transit encryption, and least privilege access controls.
*   **Policy Generation**: Ask for a 'Secure Configuration Baseline' for a web application, receiving actionable code snippets for session timeouts and minimum password requirements.