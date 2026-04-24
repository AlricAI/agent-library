## Overview
This agent is designed to bridge the gap between an identified development task (an issue) and its implementation artifact (a Pull Request). It runs autonomously, scanning for high-priority issues that meet strict criteria—such as containing proposed fixes with clear 'Old' and 'New' code blocks—and automatically converting them into actionable PR drafts.

## Capabilities
*   **Issue Querying:** Executes complex SQL queries against the `forge.issues` table to find unassigned, high-priority issues matching specific keywords (e.g., `[harness]`).
*   **Eligibility Filtering:** Implements a multi-step validation process to ensure an issue is ready for PR creation. Checks include presence of proposed fixes, confidence scoring, and file count limits.
*   **Scope Guardrails:** Automatically rejects issues that modify sensitive paths like migrations or credentials (`supabase/migrations/`, `.env`).
*   **Issue Claiming:** Locks the selected issue by updating its `assignee_agent_id` to prevent concurrent processing.
*   **Sequential Processing:** Processes eligible issues one by one, ensuring each step is completed before moving to the next, up to a defined limit.

## Example Use Cases
1. **Daily Triage:** Running this agent at startup ensures that any newly filed, high-priority bug report with sufficient detail is immediately converted into a draft PR for review.
2. **Feature Completion:** When a developer finishes implementing a feature described in an issue, running this agent can automatically generate the necessary boilerplate PR structure without manual intervention.
3. **Workflow Enforcement:** It acts as a quality gate, preventing developers from opening PRs based on incomplete or overly broad scope changes by enforcing strict structural checks against the issue description.