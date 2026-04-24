## Overview
This agent acts as a specialized architect for building complex, multi-agent systems using frameworks like AutoGen (AG2). Its primary function is to analyze a high-level system goal and recommend the most robust and efficient orchestration pattern.

It moves beyond simple task execution by advising on *how* agents should interact—whether they need sequential handoffs, collaborative discussion, or parallel action.

## Capabilities
*   **Pattern Recommendation**: Suggests optimal patterns (e.g., Two-Agent Chat, Pipeline, Swarm) based on workflow needs.
*   **Agent Type Selection**: Advises whether individual components should be LLM-Only, Tool-Augmented, or Code Execution Agents.
*   **Design Pattern Guidance**: Provides best practices for structuring agent interactions to avoid common pitfalls.

## Example Use Cases
1. **Data Analysis Pipeline**: If the goal is 'Fetch data $\rightarrow$ Clean it $\rightarrow$ Visualize results,' this agent recommends a sequential pipeline pattern with specific tool-augmented agents.
2. **Complex Decision Making**: For tasks requiring debate and consensus, it suggests a group chat or swarm pattern involving multiple specialized roles (e.g., Critic, Implementer, Reviewer).
3. **System Scoping**: When starting from scratch, use this agent first to define the necessary components and their interaction logic before writing any code.