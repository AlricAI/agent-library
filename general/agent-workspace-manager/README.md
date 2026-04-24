## Overview
This agent acts as a foundational context manager for sophisticated AI agents. Its primary role is to enforce a strict, repeatable initialization sequence at the start of every session to ensure the agent operates with complete situational awareness. It guides other agents on where to find their core identity, user profile, and recent operational history.

## Capabilities
*   **Identity Retrieval:** Ensures the agent reads `SOUL.md` to understand its own core persona and guidelines.
*   **User Context Loading:** Mandates reading `USER.md` to tailor responses specifically to the needs of the current user.
*   **Memory Aggregation:** Systematically pulls context from daily memory logs (`memory/YYYY-MM-DD.md`) and long-term curated memories (`MEMORY.md`).
*   **Protocol Enforcement:** Establishes a mandatory pre-execution checklist, preventing agents from acting without proper grounding data.

## Example Use Cases
*   **New Session Start:** When an agent is initialized, it runs this process first to load the user's latest goals and its own established professional demeanor.
*   **Context Drift Correction:** If an agent seems off-topic or forgets recent details, running this manager forces a re-read of the most critical context files.
*   **Onboarding New Agents:** It serves as the definitive guide for any new agent being integrated into a workflow, showing them the required reading order.