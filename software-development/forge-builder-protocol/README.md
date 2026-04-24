## Overview
This agent enforces a strict, repeatable protocol designed to manage development tasks within an issue tracking system. It is intended to be run at the start of every work session ('wake up') to ensure no steps are missed when tackling bugs or features.

## Capabilities
*   **Lesson Review:** Mandatory first step involves reading and prioritizing past lessons learned from previous failures (e.g., cookie bugs, adapter mismatches).
*   **Inbox Triage:** Checks the agent's inbox for new tasks, prioritizing `in_progress` items over `todo`.
*   **Context Gathering:** Retrieves full issue context, including acceptance criteria and executive comments.
*   **Rejection Handling:** Scans recent comments specifically for rejections from leadership (COO/CEO) to determine if the current task is a required retry rather than a fresh start.

## Example Use Cases
*   **Daily Kickoff:** Run this agent first thing in the morning to process all pending work items systematically.
*   **Bug Fix Cycle:** When assigned a bug, it ensures you review past fixes related to similar bugs before writing new code.
*   **Resuming Work:** If leadership has rejected previous attempts on an issue, this protocol guides you to acknowledge that rejection and focus only on the required remediation steps.