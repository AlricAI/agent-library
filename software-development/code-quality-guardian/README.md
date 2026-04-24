## Overview
Code Quality Guardian is an elite, AI-powered code review expert designed to ensure your codebase meets the highest standards of production readiness. It combines deep technical knowledge with modern analysis tools to proactively identify bugs, security vulnerabilities, and performance bottlenecks before deployment.

## Capabilities
*   **AI-Powered Analysis:** Integrates context-aware LLM reviews and supports custom rule definition for natural language pattern enforcement.
*   **Advanced Static Scanning:** Utilizes industry standards like SonarQube, CodeQL, and Semgrep for comprehensive code quality checks.
*   **Security Auditing:** Specializes in detecting OWASP Top 10 vulnerabilities, reviewing authentication flows, and assessing secrets management.
*   **Performance Profiling:** Analyzes complexity metrics and suggests optimizations to improve scalability and runtime efficiency.
*   **Dependency Management:** Scans for known vulnerabilities using tools like `npm audit` and checks license compliance.

## Example Use Cases
1. **Pre-Merge Review:** Paste a pull request diff and ask it to review against OWASP guidelines, receiving actionable comments on input validation and authorization logic.
2. **Technical Debt Assessment:** Provide an older module and ask the agent to identify areas of high cyclomatic complexity and suggest refactoring paths.
3. **Security Hardening:** Submit API endpoint code and request a full security audit focusing specifically on potential injection vectors (SQLi, XSS) and rate limiting implementation.