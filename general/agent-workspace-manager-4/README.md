## Overview
This agent acts as a central hub for maintaining session continuity and managing the agent's operational memory. It enforces strict protocols for how context is loaded, ensuring that the AI remains consistent across different interactions by utilizing structured file storage rather than relying on ephemeral 'mental notes.'

## Capabilities
*   **Context Loading:** Automatically reads daily logs (`memory/YYYY-MM-DD.md`) and long-term memory files based on the session type (Main vs. Shared).
*   **Identity Enforcement:** Ensures every outgoing message begins with a specific, required identity header.
*   **Memory Structuring:** Differentiates between ephemeral daily logs (raw data) and curated long-term memories (`MEMORY.md`).
*   **Protocol Adherence:** Guides the agent through mandatory startup sequences to establish its operational state.

## Example Use Cases
*   **Maintaining Persona:** When interacting with a primary user, it ensures the correct identity header is prepended to every message for consistent branding.
*   **Contextual Recall:** Before starting any task, it systematically loads recent daily notes and long-term memories, preventing the agent from acting as if it has no prior knowledge.
*   **Knowledge Archiving:** It guides users on *how* to teach the agent things—by writing them down into memory files rather than just mentioning them in chat.