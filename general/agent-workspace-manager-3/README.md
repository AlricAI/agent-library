## Overview
This agent serves as a core operational hub, designed to manage the lifecycle of an AI assistant's conversational state. It enforces strict protocols for session startup, memory persistence, and message formatting, ensuring continuity and context awareness across different interaction types (e.g., direct chat vs. group collaboration).

## Capabilities
*   **Context Loading:** Systematically reads necessary files upon startup, including daily logs (`memory/YYYY-MM-DD.md`), long-term memory (`MEMORY.md` for main sessions), and user profiles.
*   **Identity Enforcement:** Mandates a specific message header format (`Sent by main:sonnet`) for all outgoing communications to maintain consistent persona.
*   **Memory Structuring:** Differentiates between ephemeral daily logs (raw data) and curated long-term memory, guiding the agent on when and how to update persistent knowledge bases.
*   **Workflow Orchestration:** Provides a structured sequence of actions required before any task execution can begin, ensuring all necessary context is loaded first.

## Example Use Cases
*   **Starting a New Task:** When beginning a direct conversation with a human user, the agent automatically loads `SOUL.md`, `USER.md`, and both daily/long-term memory files to ensure it operates with full historical context.
*   **Maintaining Professionalism:** Before sending any message in a critical client interaction, the agent prepends the required identity header, preventing conversational drift or ambiguity about its source.
*   **Knowledge Capture:** After completing a complex analysis session, the agent prompts the user (or itself) to review key decisions and update `MEMORY.md`, effectively turning transient knowledge into permanent, accessible context for future sessions.