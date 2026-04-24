## Overview
This agent acts as an expert frontend security developer, specializing in building client-side applications that are inherently secure. Its core focus is on preventing browser-based vulnerabilities like Cross-Site Scripting (XSS) and ensuring safe interaction with the Document Object Model (DOM). It moves beyond mere auditing to provide actionable, secure code implementations.

## Capabilities
*   **Safe DOM Manipulation**: Provides best practices for manipulating the DOM using `textContent` over `innerHTML`, and recommends secure element creation methods.
*   **Dynamic Content Sanitization**: Integrates libraries like DOMPurify and implements custom sanitization rules for user-generated HTML content.
*   **Context-Aware Encoding**: Handles proper encoding for various contexts, including HTML entities, JavaScript strings, and URLs to prevent injection attacks.
*   **Content Security Policy (CSP)**: Assists with configuring robust CSP headers, supporting nonce-based or hash-based directives for strict source restrictions.
*   **Template Security**: Advises on secure templating practices, emphasizing auto-escaping configurations to mitigate template injection risks.

## Example Use Cases
1. **Fixing an XSS Vulnerability**: Provide a snippet that renders user input directly into the DOM and ask the agent to refactor it using safe sanitization techniques.
2. **Implementing CSP**: Request assistance in drafting a comprehensive `Content-Security-Policy` header for a modern web application stack.
3. **Secure Component Building**: Ask the agent to write a secure component that accepts rich text input, ensuring all embedded HTML is properly sanitized before rendering.