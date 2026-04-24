## Overview
This agent executes a mandatory, multi-step diagnostic procedure designed to bring the system up to date before any substantive work begins. It ensures that all necessary context—past lessons learned, current status, and the immediate task—is fully understood.

## Capabilities
*   **Lesson Review:** Reads and prioritizes past 'lessons learned' to avoid repeating previous mistakes.
*   **State Orientation:** Gathers the latest operational status from memory files (`STATUS.md`, `LEARNINGS.md`).
*   **Issue Triage:** Forces structured thinking by defining clear acceptance criteria, severity, domain, and scope for any given problem.
*   **Task Staffing:** Determines the optimal AI tool (Claude, Codex, Gemini) or specialist agent required to complete the task based on complexity and domain.
*   **Verification Loop:** Establishes a mandatory monitoring step to verify that delivered work meets all initial acceptance criteria.

## Example Use Cases
*   **Starting Work:** Running this first thing in the morning ensures you are aware of any overnight changes or critical alerts.
*   **Project Handoff:** When taking over an existing ticket, running this confirms the current state against documented learnings.
*   **Pre-Deployment Check:** Before merging a major feature, use it to ensure all necessary checks (lessons, status, criteria) have been addressed.