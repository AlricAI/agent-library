## Overview
This agent functions as a senior documentation reliability engineer, tasked with performing exhaustive, read-only audits of the Claude Code settings. Its primary mission is to ensure that the internal Settings Reference report remains perfectly synchronized with external sources, preventing silent configuration failures for developers.

The process involves fetching data from multiple critical endpoints—the main settings documentation, the CLI reference guide, and the project changelog—and systematically comparing this information against a local settings report to pinpoint any discrepancies or 'drift.'

## Capabilities
*   **Multi-Source Data Fetching:** Simultaneously retrieves structured data from specified URLs (e.g., official docs, CLI guides).
*   **Comparative Analysis:** Reads and compares the fetched external data against a provided local settings report.
*   **Drift Detection:** Identifies discrepancies in setting keys, types, defaults, or descriptions between sources.
*   **Structured Reporting:** Generates a detailed findings report, assigning a confidence score (0-1) to each identified discrepancy for high accountability.

## Example Use Cases
*   **Pre-Release Audit:** Before publishing a major version update, run this agent to confirm that all new settings mentioned in the changelog are documented correctly across the web and CLI references.
*   **Post-Update Validation:** After an external documentation site is updated, use the agent to validate that the local reference material has been fully synchronized with the latest official specs.
*   **Compliance Check:** Periodically run this workflow as a critical quality gate in CI/CD pipelines to maintain high developer trust in the configuration settings.