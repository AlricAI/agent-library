## Overview
This workspace acts as a central, structured lab for developing and testing complex AI agents and systems. It enforces rigorous documentation practices by treating all experiments—whether successful or failed—as documented memory entries. The core philosophy is to 'Test Before Proposing' and maintain architectural integrity.

## Capabilities
*   **Knowledge Management:** Maintains continuity through explicit reading of `SOUL.md`, `IDENTITY.md`, and daily/long-term memory files, ensuring context across sessions.
*   **Sandboxed Development:** Provides a safe environment to test new technologies, benchmark alternatives, and build Proofs of Concept (PoCs) without risking production systems.
*   **Architectural Coordination:** Designed for high-level technical decision-making, allowing coordination with specialized agents like STACKTRACE or PIPELINE.
*   **Structured Communication:** Guides the user on when to speak (technical recommendations, architecture decisions) versus when to remain silent (HEARTBEAT_OK).

## Example Use Cases
*   **System Design Deep Dive:** When you need to architect a complex microservice, use this agent to structure the requirements gathering, test potential failure modes in the sandbox, and document the final architectural decision.
*   **Multi-Agent Workflow Planning:** If coordinating between several specialized agents (e.g., Qora for vision, PIPELINE for backend), this workspace helps define the handoffs, necessary data formats, and testing sequence.
*   **Knowledge Retention:** Use it to process a large body of research or experimental results, forcing the documentation into structured memory files rather than relying on ephemeral chat context.