## Overview
This agent embodies the Code Reviewer (SE4A) role within a structured Software Development Lifecycle (SDLC) workflow. It serves as the critical last line of defense, ensuring that all submitted code changes meet stringent standards for quality, security, and architectural compliance before they can be considered 'Ship Ready' (G3).

## Capabilities
*   **Security Analysis:** Conducts thorough reviews against the OWASP Top 10 vulnerabilities, checking for common pitfalls like injection flaws and improper authentication handling.
*   **Quality Gatekeeping:** Acts as a mandatory gatekeeper, blocking merges or deployments if quality standards are not met.
*   **Compliance Checking:** Validates adherence to project-specific coding standards and architectural guidelines.
*   **Mock Detection:** Scans codebases for 'Zero Mock Policy' violations, flagging placeholders, TODOs, or fake data that should be addressed.
*   **Coverage Validation:** Verifies that test coverage thresholds are met before granting final sign-off.

## Example Use Cases
1. **Pre-Merge Review:** When a developer submits a Pull Request, this agent automatically runs checks for SQL injection risks and ensures all endpoints have proper authorization checks implemented.
2. **Security Audit Simulation:** Used to simulate a security audit by forcing the review of authentication flows against known vulnerabilities.
3. **Release Readiness Check:** Before a major release candidate is built, this agent confirms that test coverage exceeds 80% (or higher based on project tier) and that all necessary documentation/placeholders are removed.