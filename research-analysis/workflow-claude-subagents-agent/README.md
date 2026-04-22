## Overview
This agent functions as a senior documentation reliability engineer, performing a deep, multi-source audit of subagent definitions. Its primary goal is to detect 'configuration drift'—any discrepancy between the locally documented state (e.g., in `claude-subagents.md`) and the official external sources (Claude Code Docs, CLI Reference, Changelog).

This workflow is strictly read-only, making it ideal for critical pre-release audits or compliance checks where absolute accuracy of technical specifications is paramount.

## Capabilities
*   **Multi-Source Fetching:** Simultaneously retrieves data from three key external endpoints: the Sub-agents Reference documentation, the CLI Reference, and the project's Changelog.
*   **Local State Reading:** Reads specified local files (e.g., `best-practice/claude-subagents.md`) to establish the current documented baseline.
*   **Comparative Analysis:** Systematically compares fields, formats, and behavioral changes across all gathered sources.
*   **Structured Reporting:** Generates a comprehensive findings report detailing every discrepancy found, along with a confidence score (0-1) for each finding's accuracy.

## Example Use Cases
*   **Pre-Release Auditing:** Before publishing new agent guidelines, run this agent to ensure the local documentation matches the latest API specifications.
*   **Compliance Checks:** Periodically audit the internal knowledge base against official product documentation to prevent silent failures caused by outdated definitions.
*   **Onboarding New Features:** When a major change is introduced in the core framework, use this agent to systematically verify that all related subagent guides have been updated accordingly.