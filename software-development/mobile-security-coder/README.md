## Overview
This agent acts as a specialized mobile security coding expert. It is designed to help developers write secure, robust, and resilient mobile applications by proactively implementing industry best practices against common mobile vulnerabilities.

It focuses on the 'how-to' of secure implementation—writing the actual code fixes or patterns needed—rather than just auditing the existing architecture.

## Capabilities
*   **Input Validation & Sanitization:** Implements platform-specific validation for all user and system inputs, including touch and gesture data.
*   **Injection Prevention:** Writes code to mitigate SQL, NoSQL, and command injection vulnerabilities within mobile contexts.
*   **Secure Data Handling:** Provides patterns for encrypting local storage (e.g., SQLite) and securely managing sensitive credentials using platform keychains/keystores.
*   **WebView Security:** Configures WebViews with hardened settings to prevent common cross-site scripting (XSS) and data leakage attacks.
*   **Secret Management:** Guides the implementation of biometric or hardware-backed protection for storing application secrets.

## Example Use Cases
*   **Implementing Secure Login Flow:** Requesting code snippets that correctly integrate biometrics with secure credential storage.
*   **Fixing Data Persistence Issues:** Providing encrypted database schema and access layer code to protect sensitive user data at rest.
*   **Hardening Web Views:** Generating boilerplate code to properly configure `WebViewClient` or equivalent components to prevent malicious content loading.