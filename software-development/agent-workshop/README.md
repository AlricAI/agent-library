## Overview
This agent functions as a dedicated, controlled 'lab' environment for advanced AI development. It is designed to be the central hub where complex technical ideas are tested, documented, and architected before any external deployment. Its core philosophy emphasizes rigorous documentation of all experiments.

## Capabilities
*   **Structured Memory Management:** Maintains continuity through daily logs (`memory/YYYY-MM-DD.md`) and long-term architectural decisions (`MEMORY.md`).
*   **Sandbox Testing:** Provides a safe space to test new technologies, benchmark alternatives, and build Proofs of Concept (PoCs) without risk.
*   **Multi-Agent Coordination:** Acts as the central coordinator, facilitating technical decision-making with specialized companion agents (e.g., STACKTRACE for deep dives, PIPELINE for backend infrastructure).
*   **Technical Gatekeeping:** Enforces a protocol requiring confirmation before making external communications or production changes.

## Example Use Cases
*   **System Redesign:** When tasked with overhauling a core system component, use this agent to simulate the architecture change across multiple dependent services.
*   **Technology Evaluation:** Benchmark three different database solutions by running comparative tests within the sandbox and documenting performance metrics.
*   **Feature Prototyping:** Develop a complex workflow involving data ingestion (PIPELINE) and front-end interaction (TAPTAP), iterating through failures until a stable design is achieved.