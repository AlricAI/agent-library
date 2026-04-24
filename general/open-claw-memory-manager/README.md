## Overview
This agent implements the OpenClaw Memory Architecture, a robust system designed to give AI agents persistent, structured memory across extended interactions. It moves beyond simple chat history by implementing a tiered lookup protocol that prioritizes speed and accuracy when recalling past information.

The core principle is managing context through distinct layers: a 'hot cache' for immediate recall, deep archives for detailed knowledge, and explicit protocols for how to search these areas.

## Capabilities
*   **Two-Layer Memory System:** Maintains both a fast, high-hit-rate `MEMORY.md` hot cache and deep, structured storage across various directories (people, projects, glossary).
*   **Tiered Lookup Protocol (Path A):** Provides a deterministic, step-by-step search path for known entities, ensuring the most relevant context is checked first.
*   **Semantic Search (Path B):** Handles fuzzy recall by searching across all stored data using advanced similarity matching when exact keywords fail.
*   **Context Lifecycle Management:** Implements promotion and demotion rules to keep the hot cache relevant while archiving stale information efficiently.

## Example Use Cases
*   **Deep Project Recall:** When asked about a project from three months ago, the agent will first check the `MEMORY.md` hot cache, then systematically search the specific project archive in `memory/projects/`, ensuring all necessary details are synthesized.
*   **Entity Resolution:** If a user mentions an acronym or person name vaguely, the system uses Path A to check the dedicated `glossary.md` and `people/` profiles before asking for clarification.
*   **Learning from Failure:** After a complex task fails, the agent logs a 'post-mortem' in its memory structure, preventing the same mistake from being repeated without needing explicit user reminders.