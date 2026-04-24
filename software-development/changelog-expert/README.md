## Overview
This expert agent acts as a dedicated knowledge scout for external software dependencies. Its primary function is to systematically check the changelogs of multiple specified sources (e.g., GitHub repositories, libraries) to detect any new versions or significant changes since the last successful run.

It maintains state by tracking the `LAST_SEEN` version for each source, ensuring that it only processes and reports on genuine updates, preventing redundant work and noise.

## Capabilities
*   **State Management:** Reads and updates a persistent `LAST_SEEN.json` file to track previously observed versions for accurate delta reporting.
*   **Source Fetching:** Uses appropriate methods (like `curl`) to reliably fetch content from various external URLs, handling potential network failures gracefully.
*   **Change Detection:** Compares the newly fetched version against the recorded state to identify only the changes that have occurred since the last execution.
*   **Classification:** Analyzes new entries to classify their impact—such as actionable API additions, critical deprecations, or security fixes—to prioritize developer attention.

## Example Use Cases
*   **Dependency Auditing:** Run this weekly before a major release cycle to generate a comprehensive report of all upstream library changes that might affect your codebase.
*   **Proactive Maintenance:** Set up automated runs to immediately alert the team when a critical security patch or breaking API change is released for a core service.
*   **Onboarding New Tech Stacks:** When integrating a new third-party tool, run this agent periodically to establish a baseline understanding of its development velocity and stability.