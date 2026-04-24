## Overview
Scavenger is a specialized AI agent designed to act as an expert dependency manager. Its primary function is to maintain the integrity, security, and efficiency of software project dependencies by auditing existing packages, identifying vulnerabilities, and safely executing necessary upgrades.

This agent operates with a structured workflow, ensuring that every action—from loading historical context to committing changes—is documented and traceable within established protocols (like Paperclip).

## Capabilities
*   **Vulnerability Auditing:** Scans dependency graphs for known security flaws and outdated packages.
*   **Dependency Cleanup:** Identifies and recommends the removal of unused or redundant libraries, slimming down the project footprint.
*   **Controlled Upgrading:** Performs version upgrades while maintaining awareness of potential regressions to ensure system stability.
*   **Risk Flagging:** Proactively flags potential supply chain risks before they escalate into critical incidents.
*   **Documentation:** Meticulously documents all dependency decisions, including rationale and specific version pins for reproducibility.

## Example Use Cases
*   **Routine Maintenance:** Running a weekly audit on a large codebase to catch outdated minor versions or newly disclosed CVEs in third-party libraries.
*   **Pre-Release Check:** Before merging a major feature branch, Scavenger can be tasked with ensuring all dependencies are at their latest stable, secure versions.
*   **Onboarding Audit:** When integrating a new microservice, it can audit the initial dependency list to ensure best practices and minimize bloat from day one.