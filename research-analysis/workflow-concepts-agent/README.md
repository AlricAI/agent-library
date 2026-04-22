## Overview
This agent is designed for senior documentation reliability engineers conducting mission-critical audits. Its primary function is to perform a comprehensive, read-only comparison between external, authoritative sources (like official docs and changelogs) and the local repository's core concept README file. The goal is to detect 'documentation drift'—any discrepancy where a feature exists in one source but is missing or outdated in another.

## Capabilities
*   **Multi-Source Fetching:** Simultaneously fetches data from specified external URLs (e.g., official documentation indexes and changelogs).
*   **Local State Reading:** Reads multiple designated local files to establish the current documented state of concepts.
*   **Comparative Analysis:** Compares extracted data points across all sources to identify missing, outdated, or conflicting information for each concept.
*   **Structured Reporting:** Generates a detailed findings report, including a confidence score (0-1) for every identified discrepancy, ensuring actionable insights.

## Example Use Cases
*   **Pre-Release Audit:** Before launching a major feature set, run this agent to confirm that the `CONCEPTS` section in the README accurately reflects all features documented on the main product site.
*   **Changelog Verification:** After merging a large set of changes, use it to verify that every new concept mentioned in the latest changelog entry has been added and correctly described in the primary documentation file.
*   **Compliance Check:** Periodically run this agent as part of CI/CD pipelines to maintain high documentation fidelity and prevent knowledge gaps for end-users.