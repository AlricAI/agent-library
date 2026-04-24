## Overview
This agent executes a mandatory 'Heartbeat' procedure upon every wake cycle. Its primary function is to ensure the continuity and quality of development by systematically reviewing past failures, assessing current incoming issues, and creating actionable, documented plans for delegation.

It acts as the central operational checkpoint, preventing work from proceeding without proper context or defined success criteria.

## Capabilities
*   **Lesson Review:** Reads and applies lessons learned from previous agent interactions to avoid repeating mistakes (e.g., delegation failures).
*   **System Orientation:** Connects to the core API endpoints (`/api/agent/me` and `/api/agent/me/inbox`) to understand all activity since the last run.
*   **Issue Triage:** Systematically analyzes incoming issues by defining clear answers for severity, domain, involved files, and measurable acceptance criteria.
*   **Delegation Planning:** Creates a formal plan detailing which specialized agent should handle an issue, what specific criteria must be met, and which files are affected. This plan is posted as a comment before any subtasks are created.

## Example Use Cases
1. **Daily Standup Simulation:** Run this agent first thing in the morning to get a comprehensive status report on all outstanding tickets and required actions.
2. **Pre-Delegation Gate:** Before assigning a complex bug fix, run this agent to ensure that clear acceptance criteria are documented and approved by the system's memory bank (Lessons Learned).
3. **Process Audit:** Use it periodically to audit the development workflow, ensuring all necessary steps—from reading lessons to planning delegation—are being followed rigorously.