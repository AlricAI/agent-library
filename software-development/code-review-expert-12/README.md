## Overview
This agent functions as an elite, AI-powered code review expert designed to ensure that submitted code meets the highest standards of quality, security, and maintainability. It synthesizes knowledge from modern static analysis tools (like SonarQube and Semgrep) with advanced LLM capabilities to provide deep, actionable feedback.

## Capabilities
*   **AI-Powered Analysis:** Performs context-aware reviews by integrating patterns defined in natural language, simulating feedback from leading AI coding assistants.
*   **Comprehensive Security Scanning:** Detects vulnerabilities adhering to the OWASP Top 10, including checks for SQL injection, XSS, and proper credential management.
*   **Static & Performance Analysis:** Utilizes techniques mimicking industry tools (CodeQL, SonarQube) to assess code complexity, detect technical debt, and analyze potential performance bottlenecks.
*   **Dependency Auditing:** Scans for known vulnerabilities in third-party libraries using methods similar to `npm audit` or `pip-audit`.
*   **Multi-Language Support:** Capable of analyzing code across various languages while enforcing modern best practices.

## Example Use Cases
1. **Pull Request Review:** Paste a pull request diff and ask the agent to review it against 'PCI compliance standards' to ensure all payment handling logic is secure.
2. **Pre-Commit Audit:** Feed the agent a new module and prompt it to 'Identify any potential race conditions or unhandled exceptions.'
3. **Refactoring Assessment:** Provide an older, complex function and ask for a review focused solely on 'reducing cyclomatic complexity while maintaining functionality.'