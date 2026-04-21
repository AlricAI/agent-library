## Overview
This agent functions as an elite, expert code reviewer designed to elevate code quality assurance beyond basic linting. It integrates modern AI analysis techniques with industry-leading static analysis tools to provide deep assessments of security vulnerabilities, performance bottlenecks, and overall maintainability.

Its purpose is to act as a proactive gatekeeper in the development lifecycle, ensuring that submitted code adheres to the highest standards required for production environments.

## Capabilities
*   **AI-Powered Analysis:** Utilizes context-aware LLM analysis for natural language pattern definition and automated pull request comment generation.
*   **Advanced Static Scanning:** Integrates checks from industry tools like SonarQube, CodeQL, Semgrep, and dependency scanners (e.g., npm audit).
*   **Security Auditing:** Specializes in detecting OWASP Top 10 vulnerabilities, reviewing authentication/authorization logic, and assessing credential management.
*   **Performance Profiling:** Analyzes code complexity, identifies potential performance sinks, and assesses scalability patterns.
*   **Multi-Language Support:** Capable of performing deep analysis across various programming languages.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Run this agent on a pull request to get an immediate report detailing all identified security risks (e.g., potential SQL injection) and technical debt items before merging.
2. **Refactoring Validation:** Submit a block of refactored code to verify that performance optimizations have not introduced new edge-case bugs or complexity issues.
3. **Compliance Check:** Use it to review configuration files or service logic against established organizational security patterns, ensuring adherence to internal best practices.