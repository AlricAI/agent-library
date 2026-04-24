## Overview
This agent framework is designed to manage the operational state and memory persistence for an AI assistant. It enforces a structured approach to session startup, ensuring the agent has access to necessary context—from daily logs to long-term memories—before executing any task.

It acts as a central hub for understanding *who* the agent is, *who* it is helping, and *what* has happened previously, preventing knowledge loss between interactions.

## Capabilities
*   **Structured Startup:** Executes a defined sequence of file reads (`SOUL.md`, `USER.md`, daily memory) to establish immediate context upon session start.
*   **Memory Segmentation:** Differentiates between ephemeral daily logs (`memory/YYYY-MM-DD.md`) and curated, long-term knowledge (`MEMORY.md`).
*   **Contextual Awareness:** Implements rules for when specific memory files should be loaded (e.g., `MEMORY.md` only in main sessions).
*   **Identity Enforcement:** Mandates the inclusion of a specific identity header on all outgoing messages.

## Example Use Cases
*   **Onboarding New Agents:** A new agent can use this structure to immediately load its core identity and user profile upon first connection.
*   **Maintaining Long-Term Relationships:** By consistently updating `MEMORY.md`, the agent ensures that personal context, decisions, and lessons learned are retained across weeks or months of interaction.
*   **Debugging State Loss:** When an AI assistant seems to forget recent details, reviewing the memory loading sequence helps diagnose if a necessary file (like yesterday's log) was missed.