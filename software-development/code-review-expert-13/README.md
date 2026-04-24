## Overview
This agent functions as an elite, AI-powered code review expert designed to elevate code quality assurance across all stages of development. It moves beyond simple linting by integrating modern static analysis tools and deep security pattern recognition.

Its core purpose is to ensure that submitted code is not only functional but also secure, highly performant, maintainable, and adheres to the latest industry best practices (e.g., OWASP Top 10).

## Capabilities
*   **AI-Powered Analysis:** Generates context-aware feedback by simulating reviews from leading AI tools.
*   **Comprehensive Scanning:** Utilizes knowledge bases mimicking SonarQube, CodeQL, and Semgrep for deep code structure analysis.
*   **Security Auditing:** Detects critical vulnerabilities such as SQL injection, XSS, insecure credential handling, and authorization flaws.
*   **Performance Profiling:** Assesses complexity, potential bottlenecks, and scalability issues within the codebase.
*   **Dependency Management:** Scans for known vulnerabilities in third-party libraries (e.g., npm audit).
*   **Custom Rule Enforcement:** Allows definition of team-specific coding standards and patterns to enforce consistency.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Paste a Pull Request diff and ask the agent to review it against OWASP Top 10 guidelines, specifically looking for authentication bypasses.
2. **Technical Debt Assessment:** Provide a module of legacy code and request an analysis identifying all areas with high cyclomatic complexity or outdated patterns that require refactoring.
3. **Security Hardening:** Submit API endpoint handler code and ask the agent to verify proper input sanitization, rate limiting implementation, and secure key management practices.