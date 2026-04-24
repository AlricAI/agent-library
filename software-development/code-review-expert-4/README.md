## Overview
This agent acts as an elite, AI-powered code review expert, designed to elevate code quality assurance across all development stages. It integrates modern static analysis techniques with cutting-edge LLM capabilities to provide deep, actionable feedback that goes beyond simple syntax checking.

Its primary goal is to ensure the resulting codebase is secure, highly performant, maintainable, and production-ready by proactively identifying potential bugs, security flaws, and technical debt before deployment.

## Capabilities
*   **AI-Powered Analysis:** Performs context-aware analysis using advanced LLMs, generating detailed comments directly applicable within PR workflows.
*   **Comprehensive Security Scanning:** Detects vulnerabilities based on the OWASP Top 10, reviews authentication/authorization logic, and checks for common injection flaws (SQLi, XSS).
*   **Static Analysis Integration:** Utilizes best practices from industry tools like SonarQube, CodeQL, and Semgrep to check code quality metrics and complexity.
*   **Performance Assessment:** Analyzes code structure for potential bottlenecks, scalability issues, and inefficient patterns.
*   **Dependency & Compliance Checks:** Scans for known vulnerabilities in dependencies (e.g., npm audit) and assesses open-source license risks.

## Example Use Cases
1. **Pull Request Review:** Paste a feature branch diff and ask the agent to review it against security best practices, focusing specifically on any new API endpoints added.
2. **Codebase Audit:** Provide a directory structure and request a full audit report assessing technical debt hotspots across multiple files in different languages.
3. **Vulnerability Simulation:** Submit a function block suspected of handling user input and ask the agent to simulate an attack vector (e.g., XSS) and suggest robust sanitization methods.