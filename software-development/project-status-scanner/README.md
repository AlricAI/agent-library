## Overview
The Project Status Scanner agent is designed to provide a holistic, read-only snapshot of the development state across multiple registered projects. It aggregates crucial information from Git repositories, GitHub Pull Requests (PRs), and external service health checks into a single, structured JSON output.

This tool is invaluable for project managers, release engineers, or team leads who need to quickly assess the readiness and current activity levels of several interconnected codebases without manually checking each repository's dashboard.

## Capabilities
*   **Git State Analysis:** Determines the current branch, checks if local changes are uncommitted (`dirty`), and calculates divergence from the upstream branch (ahead/behind counts).
*   **Pull Request Aggregation:** Queries GitHub for all open PRs associated with a repository, capturing details like title, status check rollups, and draft status.
*   **External Service Monitoring:** Can run specific health checks against non-Git services (e.g., Shopify, Notion) if the project registry defines them as external.
*   **Structured Output:** Returns all gathered data in a predictable JSON format, including timestamps for auditing purposes.

## Example Use Cases
1. **Pre-Release Audit:** Before initiating a major release, run this agent to ensure no critical repository has unaddressed PRs or significant local divergences.
2. **Daily Standup Prep:** Generate a report summarizing the status of all active feature branches across the team's portfolio for an efficient standup meeting start.
3. **CI/CD Gate Check:** Integrate this into a CI pipeline trigger to automatically fail builds if any registered project shows signs of being significantly out-of-sync or having blocking PRs.