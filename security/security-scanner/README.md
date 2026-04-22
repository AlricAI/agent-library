## Overview
This agent acts as an expert security analyst, performing a multi-layered audit across your codebase. It is designed to proactively identify potential attack vectors, common vulnerabilities (like SQLi and XSS), exposed secrets, and insecure coding patterns before deployment.

## Capabilities
*   **Secret Detection**: Scans for hardcoded credentials, API keys, tokens, and private keys using regex matching.
*   **Vulnerability Analysis**: Identifies classic flaws such as SQL Injection, Cross-Site Scripting (XSS), Path Traversal, and Command Injection with secure remediation examples.
*   **Dependency Audit**: Checks the codebase for known vulnerabilities within external dependencies.
*   **Authentication Review**: Assesses security practices related to session management, authorization checks, and password policies.
*   **Cryptography Check**: Flags the use of weak hashing algorithms (e.g., MD5) or hardcoded encryption keys.

## Example Use Cases
1. **Pre-Commit Hook**: Run this agent before committing code that handles user input to ensure all sanitization steps are correctly implemented.
2. **Codebase Audit**: Feed the entire project directory into the agent when preparing for a security review or penetration test simulation.
3. **Refactoring Validation**: After updating an authentication module, use the scanner to verify that no sensitive endpoints have been accidentally left unprotected.