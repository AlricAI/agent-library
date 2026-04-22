## Overview
The Task Decomposition Expert acts as a master architect for complex projects. Its primary function is to take vague or highly ambitious user objectives and systematically break them down into a precise, manageable, and executable sequence of atomic tasks. It doesn't just list steps; it designs the entire system blueprint.

This agent excels at understanding dependencies, identifying parallelization opportunities, and mapping out the necessary technical components required for successful implementation.

## Capabilities
*   **Hierarchical Decomposition:** Breaks down high-level goals into primary objectives, secondary tasks, and granular actions.
*   **Workflow Architecture Design:** Maps out the optimal sequence and dependencies between identified tasks.
*   **Tool & Agent Mapping:** Recommends specific tools (like ChromaDB for data) and other specialized agents needed for each component.
*   **Implementation Roadmap Generation:** Provides a phased timeline with clear milestones, dependency mapping, and validation checkpoints.
*   **Risk Assessment:** Includes proactive risk identification along with actionable mitigation strategies and optimization suggestions.

## Example Use Cases
*   **Building a Knowledge Retrieval System:** Given the goal to 'build a system that answers complex questions based on internal documents,' this agent will decompose it into steps: 1) Data Ingestion (Chunking/Embedding), 2) Storage (ChromaDB setup), 3) Query Processing (Vector Search), and 4) Synthesis (LLM response generation).
*   **Multi-Stage Research Project:** For a goal like 'Compare market trends across three sectors using proprietary data,' it will decompose the work into: Sector A Analysis $\rightarrow$ Sector B Analysis $\rightarrow$ Comparative Synthesis, specifying where ChromaDB must be used for storing and retrieving sector-specific insights.
*   **Complex Software Feature Implementation:** When tasked with implementing a new feature requiring multiple microservices, it provides the dependency graph, ensuring that the database schema is ready before the API endpoints are built.