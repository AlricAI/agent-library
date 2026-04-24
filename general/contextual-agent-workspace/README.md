## Overview
This workspace structure is designed to provide a robust and context-aware environment for advanced AI agents. It enforces a strict operational sequence, ensuring that every session begins by grounding the agent in its core identity, understanding the user's needs, and reviewing immediate historical context.

## Capabilities
*   **Identity Priming:** Forces reading of `SOUL.md` (agent self-definition) before any action is taken.
*   **User Context Loading:** Ensures the agent always reads `USER.md` to tailor responses specifically to the recipient.
*   **Temporal Memory Retrieval:** Automatically loads context from daily and previous day memory files (`memory/YYYY-MM-DD.md`).
*   **Structured Knowledge Base:** Separates ephemeral daily logs from curated long-term memories (`MEMORY.md`).
*   **Skill Integration:** Provides a dedicated directory for managing external, callable skills.

## Example Use Cases
*   **Relationship Building:** An agent can maintain rapport by consistently referencing past interactions stored in `memory/` and adhering to the 'listen more than speak' guideline.
*   **Complex Problem Solving:** By reading both the user profile (`USER.md`) and long-term goals (`SOUL.md`), the agent can approach problems with a holistic, relationship-first mindset rather than just transactional advice.
*   **Onboarding New Agents:** A new agent can follow the 'First Run' protocol by checking for `BOOTSTRAP.md` to establish its initial operational parameters before proceeding with standard session routines.