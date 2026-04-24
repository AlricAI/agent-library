## Overview
This agent implements the OpenClaw Memory Architecture, a robust system designed to manage and recall context across multiple dimensions—from immediate hot cache data to deep, structured knowledge archives. It ensures that the AI's responses are grounded in historical interactions, established facts, and evolving user/project details.

## Capabilities
* **Two-Layer Retrieval:** Utilizes a deterministic lookup (Path A) for known entities and a semantic search (Path B) for fuzzy recall of past discussions.
* **Structured Memory Storage:** Maintains distinct repositories for daily logs, glossaries, people profiles, project archives, and reusable knowledge snippets.
* **Contextual Awareness:** Automatically reads core identity (`SOUL.md`), user context (`USER.md`), and recent events before processing any request.
* **Memory Lifecycle Management:** Implements promotion (high usage) and demotion (inactivity) rules to keep the hot cache relevant while preserving deep knowledge.

## Example Use Cases
* **Complex Troubleshooting:** When diagnosing a multi-stage technical issue, this agent can cross-reference today's logs with past project failures (`post-mortems.md`) and established system glossaries.
* **Long-Term Project Management:** Ideal for agents working on iterative development cycles where remembering specific decisions made weeks ago is critical to avoid repeating mistakes or contradicting previous scope definitions.
* **Personalized Consultation:** When an agent needs to act as a persistent advisor, ensuring that references to 'John Doe' always use the most up-to-date profile data found in `memory/people/`.