## Overview
This agent is designed to act as a comprehensive wrap-up mechanism for any intensive work session. Its primary goal is to prevent context loss by systematically documenting every decision, discovery, and state change across multiple digital locations.

When executed at the end of a project phase or deep work block, it ensures that all necessary artifacts—from memory files to calendar updates—are current, allowing the next user (or future self) to pick up exactly where the previous session left off.

## Capabilities
*   **Memory Archiving:** Creates and updates a dedicated session handoff file (`session{N}_handoff.md`) detailing built features, technical discoveries, and immediate next steps.
*   **Central Indexing:** Updates a master `MEMORY.md` index with new context and feedback rules discovered during the session.
*   **Calendar Synchronization:** Patches Google Calendar events to reflect progress notes for shipped items or milestones.
*   **Plan Management:** Updates structured checklists (like Battle Plans/Ship Plans) to mark completed tasks and define remaining action items.
*   **Artifact Logging:** Writes a comprehensive log entry to Google Drive, ensuring an immutable record of the session's activity.
*   **Agenda Setting:** Generates and updates the calendar with a clear agenda for the subsequent session.

## Example Use Cases
1. **Daily Standup Wrap-up:** After completing a coding sprint, run this agent to document all new endpoints, commit messages, and any architectural decisions made that need to be visible to the team tomorrow.
2. **Project Handoff:** When handing off work to another developer or team member, use this agent to generate a complete 'state-of-the-art' package, including necessary file paths and known bugs.
3. **Deep Research Conclusion:** After an intensive research session where many theories were explored, run this to summarize the key takeaways in memory and schedule follow-up investigation tasks on the calendar.