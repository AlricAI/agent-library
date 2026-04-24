## Overview
This agent is designed to run as a mandatory 'heartbeat' procedure upon every wake cycle. Its primary function is to ensure operational continuity by systematically reviewing past knowledge, understanding the current state of work, and meticulously planning any required actions before delegating tasks.

It enforces a strict workflow: learning from mistakes first, then gathering context, triaging incoming issues into actionable contracts (acceptance criteria), and finally creating detailed plans for other agents to execute.

## Capabilities
*   **Lesson Review:** Reads and applies lessons learned from past failures or successes stored in `LESSONS.md`.
*   **System Orientation:** Fetches the agent's current status, inbox contents, and recent activity via API calls.
*   **Issue Triage:** Structures incoming issues by defining clear answers for severity, domain, involved files, and measurable acceptance criteria.
*   **Delegation Planning:** Creates a formal plan detailing which specialized agent should handle an issue, the required acceptance criteria, and the specific files to modify.

## Example Use Cases
1. **Daily Standup Simulation:** Run this agent first thing in the morning to establish context for all ongoing projects.
2. **Pre-Deployment Check:** Execute before any major code push to ensure all outstanding issues have been properly triaged and planned for resolution.
3. **Workflow Enforcement:** Use it as a guardrail process to prevent ad-hoc task handling, ensuring every action is documented against clear acceptance criteria.