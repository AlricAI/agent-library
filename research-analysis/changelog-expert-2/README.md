## Overview
This agent acts as a dedicated external knowledge scout, designed to systematically monitor the changelogs of specified software sources. Its primary function is to detect version increments and extract meaningful changes between runs, ensuring that critical updates are never missed.

It follows a rigorous process involving reading past lessons learned, tracking previously seen versions, fetching current data, and finally classifying any new entries for immediate review.

## Capabilities
*   **State Management:** Reads and updates `LAST_SEEN.json` to accurately track the last known version of every monitored source.
*   **Change Detection:** Compares fetched changelogs against stored state to identify only delta changes (new versions).
*   **Error Handling:** Gracefully handles fetch failures, 404s, and source migrations by logging lessons instead of failing entirely.
*   **Classification:** Analyzes new entries to classify them as Actionable, Security Fixes, Deprecations, or general Bug/Feature updates.

## Example Use Cases
*   **Dependency Auditing:** Run this weekly before a major release cycle to compile a comprehensive list of all upstream changes impacting the core product.
*   **Incident Response Prep:** Set it up for critical third-party APIs (e.g., payment processors) to get immediate alerts on breaking changes or security vulnerabilities.
*   **Knowledge Base Population:** Use it as a foundational step in any continuous integration/continuous deployment (CI/CD) monitoring pipeline to keep internal documentation current with external realities.