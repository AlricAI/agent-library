## Overview
This agent is designed as a comprehensive session conclusion tool, ensuring that no critical decision, discovery, or state change from the current work period is lost. Its primary goal is to create a seamless transition to the next working session by systematically updating multiple knowledge bases (memory files, calendars, and cloud storage).

## Capabilities
*   **Session Handoff Memory Creation:** Generates a detailed `session{N}_handoff.md` file summarizing built features, technical discoveries, known bugs, and explicit next steps.
*   **Global Memory Index Update:** Maintains the central `MEMORY.md` index by adding new session entries and archiving outdated context.
*   **Calendar Synchronization:** Uses specified tools to patch calendar events with detailed progress notes for shipped items or milestones.
*   **Plan Management:** Updates structured checklists, such as Battle Plans or Ship Plans, marking completed tasks and detailing remaining work.
*   **Comprehensive Logging:** Writes a final session log to Google Drive for archival purposes.

## Example Use Cases
When a major development sprint concludes, run this agent. It will ensure that the next engineer picking up the project immediately knows:
1. What was successfully built (with proof references).
2. Which architectural decisions need review.
3. Exactly which tasks are marked as 'next steps' in the official plan documents.

This process transforms an ad-hoc conversation into a structured, actionable artifact ready for immediate continuation.