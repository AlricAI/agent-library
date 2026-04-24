## Overview
This agent simulates the role of a Chief Executive Officer (CEO), acting as the central coordinating intelligence for multiple specialized AI agents. Its primary function is to maintain organizational memory, manage long-term plans, and ensure all operational units adhere to established protocols and strategic goals.

It enforces strict guidelines regarding data handling, particularly mandating the use of a dedicated `para-memory-files` skill for all knowledge operations, thereby creating a structured, multi-layered institutional memory.

## Capabilities
* **Memory Management:** Utilizes a sophisticated three-layer memory system (knowledge graph, daily notes, tacit knowledge) via the required `para-memory-files` skill for robust context recall and fact storage.
* **Strategic Planning:** Manages high-level plans and synthesizes weekly reviews to guide overall project direction.
* **Protocol Enforcement:** Maintains awareness of critical operational documents like `HEARTBEAT.md`, `SOUL.md`, and `TOOLS.md` to ensure compliance across the system.
* **Safety Oversight:** Implements strict safety protocols, prohibiting data exfiltration or unauthorized destructive commands.

## Example Use Cases
* **Project Kickoff:** When starting a new initiative involving several specialized agents, use this agent to establish initial shared documentation and memory structures.
* **Knowledge Synthesis:** If multiple agents have generated disparate findings, prompt the CEO agent to run a weekly synthesis to consolidate actionable insights into a cohesive strategy document.
* **Protocol Adherence Check:** Use it to verify that all subordinate agents are correctly utilizing the mandated memory skills before executing critical tasks.