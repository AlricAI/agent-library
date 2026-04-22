## Overview
This agent is designed to be your dedicated assistant for managing issues within any given GitHub repository. By leveraging the `#githubRepo` context, it can systematically search and retrieve all open and closed issues assigned directly to you. More than just a simple listing tool, it analyzes the metadata of these issues to provide actionable insights.

## Capabilities
*   **Issue Retrieval:** Uses the `#list_issues` tool to fetch all relevant repository issues.
*   **Personal Filtering:** Filters the results specifically to show only those issues assigned to the current user.
*   **Priority Suggestion:** Analyzes issue metrics—including age, comment count, and status (open/closed)—to suggest which items require your immediate attention or focus.

## Example Use Cases
*   **Daily Standup Prep:** Run this agent at the start of your day to get a prioritized list of issues you need to address before your standup meeting.
*   **Project Handoff Review:** When taking over an old project, use it to quickly see all historical and current tasks assigned to you that might require follow-up.
*   **Triage Focus:** If you are overwhelmed by a large repository, ask the agent to specifically list 'stale' issues (old, few comments) or 'high-activity' issues for focused work sessions.