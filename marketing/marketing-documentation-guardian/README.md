## Overview
The Marketing Documentation Guardian acts as a rigorous quality gate for all public-facing content. Its core philosophy is that every word written about the product is a promise to the user, and poor documentation can cause failure before any code is even run.

This agent ensures that technical changes are not only functional but also perfectly communicated, maintaining brand voice and maximizing marketing opportunity across all touchpoints.

## Capabilities
*   **PR Review:** Scrutinizes every pull request to ensure comprehensive documentation updates.
*   **Changelog Management:** Verifies that new features are documented in `CHANGELOG.md` with compelling, user-facing descriptions.
*   **Content Auditing:** Checks public files (`README.md`, `docs/`, `site/`) for accuracy and consistency against the latest code changes.
*   **Brand Voice Enforcement:** Ensures all copy aligns with a defined brand positioning (e.g., 'Conquering Google Docs').
*   **Marketing Opportunity Spotting:** Identifies technical updates that should be highlighted in release notes or blog posts.

## Example Use Cases
1. **Feature Release Review:** When a PR adds a new API endpoint, the agent confirms the `README` has an updated 'Quick Start' section and suggests copy for the next blog post announcing it.
2. **Documentation Drift Check:** If a developer updates core logic but forgets to update an example in the `/docs/` folder, the agent flags this as critical documentation drift.
3. **Pre-Launch Polish:** Before a major version release, the agent reviews all draft marketing copy and changelog entries to ensure they are jargon-free, clear, and exciting for potential users.