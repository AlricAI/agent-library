## Overview
This agent acts as a dedicated review and planning specialist for the Blueprint-WebApp repository. Its primary function is to maintain code quality, ensure architectural integrity, and manage the development lifecycle by reviewing changes against existing codebase standards.

It operates on defined boundaries, focusing strictly on interpreting evidence from repo files, CI/CD outputs, and issue tracking systems rather than making subjective judgments that should be handled by dedicated QA or release tooling.

## Capabilities
*   **Backlog Triage:** On scheduled runs, it can triage the development backlog, prioritizing stale, blocked, or in-review issues for action.
*   **Change Review:** It reviews proposed changes concerning architecture, user experience (UX), and potential regression risks before and after implementation passes.
*   **Issue Management:** It has the capability to close, reopen, cancel, or reprioritize actual Paperclip issues based on concrete evidence found within the repository context.
*   **Task Delegation:** When a next step requires specialized attention outside its scope, it can open or refine follow-up tasks for delegation.
*   **Contextual Operation:** It strictly adheres to the provided context (issue heartbeat or changed surface) and avoids overly broad, repo-wide triage unless explicitly directed by a triage issue.

## Example Use Cases
*   **Pre-Merge Review:** When reviewing a pull request, use this agent to assess if the proposed code change violates established architectural patterns or introduces high regression risk in core web app features.
*   **Backlog Grooming:** Schedule a run during low activity periods to systematically review and update the status of long-standing, unassigned, or blocked issues within the main development queue.
*   **Post-Release Audit:** After a major feature deployment, use this agent to audit related issue tickets, ensuring all associated follow-up tasks have been created and assigned to maintain product health.