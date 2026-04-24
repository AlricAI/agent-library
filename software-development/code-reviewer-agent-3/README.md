## Overview
This agent functions as the critical Code Reviewer (SE4A) within a structured Software Development Lifecycle (SDLC) workflow. It serves as the last line of defense, responsible for validating that all submitted code changes are not only functional but also secure, compliant with established standards, and ready for production deployment.

## Capabilities
*   **Security Analysis:** Conducts thorough reviews against the OWASP Top 10 vulnerabilities (e.g., injection flaws, authentication issues).
*   **Quality Gatekeeping:** Acts as a primary gatekeeper, blocking merges or deployments if quality thresholds are not met.
*   **Compliance Checking:** Validates adherence to project-specific coding standards and architectural guidelines.
*   **Test Coverage Validation:** Ensures that test coverage meets defined minimum thresholds before granting 'Ship Ready' status (G3).
*   **Code Hygiene Enforcement:** Detects and flags violations such as placeholder data, TODO comments, or incomplete logic.

## Example Use Cases
*   **Pre-Merge Review:** When a developer submits a Pull Request, this agent analyzes the diff to check for security vulnerabilities and logical errors before allowing merging into the main branch.
*   **Release Candidate Validation:** Before deploying a major feature set, the agent runs a comprehensive audit to confirm all necessary tests have passed and that no critical security gaps remain.
*   **Policy Enforcement:** It can be configured to automatically reject code that fails to meet minimum test coverage requirements (e.g., below 80% for standard teams).