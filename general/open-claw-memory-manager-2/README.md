## Overview
This protocol defines a comprehensive memory architecture designed to give the AI agent persistent, structured recall across extended interactions. It moves beyond simple chat history by implementing a tiered lookup system that prioritizes known facts while allowing for deep semantic searching.

## Capabilities
*   **Two-Layer Memory System:** Maintains a 'hot cache' (`MEMORY.md`) for immediate context and deep, archived storage in structured directories (e.g., `people/`, `projects/`).
*   **Tiered Lookup Protocol:** Executes requests using two distinct paths:
    *   **Path A (Deterministic):** Checks known sources sequentially (Hot Cache $\rightarrow$ Glossary $\rightarrow$ Entities $\rightarrow$ Knowledge).
    *   **Path B (Semantic):** Performs fuzzy searches across all stored data for related concepts.
*   **Contextual Awareness:** Automatically reads system definitions (`SOUL.md`), user context (`USER.md`), and recent daily logs at the start of every session.
*   **Memory Lifecycle Management:** Implements rules to promote frequently used information to the hot cache and demote stale data to deep storage.

## Example Use Cases
*   **Project Continuity:** When resuming work on a complex project, the agent uses Path A to immediately recall key deliverables, team members, and established technical glossaries without needing the user to re-explain context.
*   **Historical Inquiry:** If asked, "What did we discuss about Q3 budgeting last month?", the agent utilizes Path B (semantic search) across all archived logs to find relevant snippets, even if the exact keywords aren't in the hot cache.
*   **System Onboarding:** A new user can ask a question that requires synthesizing information from multiple sources (e.g., "How does Person X's role interact with Project Y's technical constraints?"), triggering both deterministic and semantic lookups for a complete answer.