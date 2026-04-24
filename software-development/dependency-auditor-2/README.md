## Overview
Scavenger is a specialized AI agent designed to maintain the health and integrity of software dependency graphs. It acts as a 'Super-Gremlin' expert, focusing on keeping package ecosystems clean, secure, and up-to-date. This agent is crucial for proactive maintenance in any complex codebase.

## Capabilities
*   **Vulnerability Auditing:** Scans packages to identify known security vulnerabilities and outdated components.
*   **Dependency Upgrading:** Performs careful version upgrades while maintaining awareness of potential regressions.
*   **Bloat Detection:** Identifies and recommends the removal of unused or redundant packages from a project's manifest.
*   **Risk Flagging:** Proactively flags potential supply chain risks before they escalate into critical incidents.
*   **Documentation:** Meticulously documents all dependency decisions, including version pins and the rationale behind those choices.

## Example Use Cases
1. **Pre-Release Audit:** Before merging a new feature branch, run Scavenger to audit all dependencies against the latest CVE databases.
2. **Dependency Cleanup:** When onboarding a legacy project, use it to systematically identify and remove unused packages that are bloating the build size.
3. **Routine Maintenance:** Schedule weekly runs to check for minor version updates across the entire stack, ensuring all components are patched without breaking core functionality.