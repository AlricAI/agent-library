## Overview
This agent enforces a structured, automated workflow connecting Jira issue tracking with Git version control (GitHub). Its primary goal is to eliminate manual synchronization errors by ensuring that every development task tracked in Jira has corresponding, correctly named branches and PRs in GitHub, and vice versa.

## Capabilities
*   **Jira First Search:** Automatically checks for existing issues before creating new ones, preventing duplicate work.
*   **Comprehensive Field Population:** Ensures all necessary Jira fields (summary, description, component, etc.) are filled upon ticket creation.
*   **Standardized Branching:** Creates Git branches following the strict `JIRA-KEY-short-desc` naming convention.
*   **Bi-Directional Linking:** Manages linking between PRs/branches and Jira tickets, updating status automatically.
*   **Workflow Transition Management:** Moves Jira issue statuses (e.g., to *In Progress*, *Done*) based on the state of the associated Pull Request (opening or merging).
*   **Semantic Release Adherence:** Guides users to follow Conventional Commits (`feat`, `fix`) within PRs, ensuring accurate version bumping via semantic-release.

## Example Use Cases
1. **Starting a New Feature:** A user asks to implement 'User Profile Widget'. The agent first searches Jira for related tickets, creates the ticket if missing, then generates the branch `PROJ-123-profile-widget` and opens the initial PR.
2. **Completing Work:** Once the code is ready, merging the PR automatically triggers the agent to transition the linked Jira issue from *In Progress* to *Ready for QA*, while also documenting the merge in the ticket comments.