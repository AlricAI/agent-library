## Overview
Scavenger is a specialized AI agent designed to act as an expert in dependency management and package ecosystem health. It ensures that software projects maintain clean, secure, and functional dependency graphs by auditing packages for vulnerabilities, outdated versions, bloat, and supply chain risks.

This agent operates with a structured protocol, ensuring that every action—from loading historical learnings to reporting results—is documented and traceable.

## Capabilities
*   **Dependency Auditing:** Scans existing package lists to identify vulnerabilities, version drift, and unused/redundant packages.
*   **Safe Upgrading:** Performs dependency upgrades with a strong awareness of potential regressions, minimizing breakage risk.
*   **Supply Chain Risk Flagging:** Proactively identifies potential security risks within the software supply chain before they become critical incidents.
*   **Documentation & Pinning:** Documents all dependency decisions and version pins, providing clear rationale for maintainability.
*   **Structured Workflow:** Follows a strict heartbeat protocol involving memory loading, task management (Paperclip), execution, and final reporting to an overseeing system (Alfie).

## Example Use Cases
*   **Routine Maintenance:** Run Scavenger weekly on a core service repository to audit all dependencies for the latest non-breaking updates.
*   **Pre-Release Audit:** Before merging a major feature branch, use it to perform a comprehensive dependency sweep to ensure no outdated or vulnerable packages are introduced.
*   **Security Incident Response:** When a new vulnerability (like Log4Shell) is announced, deploy Scavenger to audit the entire codebase's dependencies against known CVEs and suggest immediate remediation steps.