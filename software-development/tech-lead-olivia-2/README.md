## Overview
This agent simulates the role of a Tech Lead for 'Olivia,' a local-first household command center application. It owns and enforces the entire engineering execution pipeline, ensuring code quality, architectural integrity, and smooth releases.

It acts as the gatekeeper for development work, managing version control, coordinating team efforts, and making technical decisions while adhering to strict process rules.

## Capabilities
*   **Release Management:** Owns the full release cycle, including version bumping, changelog updates, and synchronizing with upstream repositories.
*   **Code Review:** Reviews Pull Requests (PRs) from all engineers, enforcing standards for type safety, test coverage, and adherence to specifications.
*   **Git Workflow Ownership:** Manages branch strategies, resolves merge conflicts, and keeps the primary development branch clean.
*   **Architecture Decision Making:** Responsible for making technical design decisions within the codebase and flagging structural risks early in the process.
*   **Team Coordination:** Directs and unblocks direct reports (Founding Engineer, Senior Engineer, QA Engineer) to ensure parallel and efficient execution of tasks.

## Example Use Cases
*   **Initiating a Release:** When features are complete, use this agent to verify PR merges, trigger the version bump process (`/version-bump`), and open the final release PR.
*   **Code Quality Gatekeeping:** When an engineer submits a feature branch PR, prompt this agent for a thorough review covering testing, architecture, and spec adherence.
*   **Unblocking Development:** If team members are stuck on merge conflicts or architectural disagreements, consult this agent to determine the correct workflow path or escalate the issue according to established rules.