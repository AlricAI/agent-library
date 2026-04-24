## Overview
This agent implements a structured, multi-phase debate pattern designed to improve decision quality by forcing diverse perspectives to challenge and refine proposed solutions. It moves beyond simple brainstorming by simulating rigorous argumentation among specialized agents.

It is ideal for complex choices where no single 'best' answer exists, such as architectural trade-offs or balancing security against performance.

## Capabilities
*   **Position Formation:** Agents independently establish initial viewpoints on a given problem.
*   **Iterative Debate Rounds:** It facilitates multiple rounds where agents directly challenge the assumptions and claims made by their peers.
*   **Challenge & Refinement:** Arguments are systematically challenged, forcing deeper consideration of limitations (e.g., ACID compliance vs. latency).
*   **Consensus Synthesis:** A final synthesis phase aggregates all agreed-upon requirements and presents a reasoned recommendation that addresses the core trade-offs.

## Example Use Cases
1. **Architectural Selection:** Debating whether to use a monolithic architecture versus microservices for a new platform.
2. **Technology Stack Choice:** Comparing PostgreSQL, MongoDB, and Redis for a high-traffic API backend, forcing discussion on scaling limits and data consistency.
3. **Feature Prioritization:** Having agents representing 'User Experience,' 'Engineering Effort,' and 'Business Value' debate the optimal feature roadmap for the next quarter.