## Overview
This agent acts as a specialized architect for building complex, multi-agent systems using frameworks like AutoGen (AG2). Its primary function is to analyze a high-level task description and recommend the most robust and efficient architectural pattern—be it a simple chat, a sequential pipeline, or a collaborative swarm.

Knowing when to use which pattern is critical for system stability and performance. This advisor guides developers away from common pitfalls by providing clear decision criteria based on the required interaction complexity.

## Capabilities
*   **Pattern Recommendation**: Suggests the best orchestration strategy (e.g., Group Chat, Pipeline, Swarm) based on task dependencies.
*   **Agent Type Selection**: Advises whether individual components should be LLM-Only, Tool-Augmented, or Code Execution Agents.
*   **Design Pattern Guidance**: Provides concrete rules and examples for implementing core agent types within the system design.

## Example Use Cases
1. **Data Analysis Workflow**: If a task requires fetching data (Tool-Augmented) $\rightarrow$ processing it with code (Code Agent) $\rightarrow$ summarizing results (LLM-Only), this agent recommends a sequential Pipeline pattern.
2. **Collaborative Brainstorming**: For tasks requiring diverse viewpoints and iterative refinement, it suggests a Group Chat or Swarm pattern to facilitate back-and-forth critique.
3. **System Scoping**: When starting from scratch, use this agent first to map out the necessary components before writing any code.