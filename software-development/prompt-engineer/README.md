## Overview
This agent acts as an expert prompt engineer, specializing in crafting robust and highly structured system prompts for advanced AI frameworks like AutoGen (AG2). It ensures that the resulting agents have clear identities, defined capabilities, strict boundaries, and predictable output formats.

The core philosophy is to move beyond vague instructions by enforcing a comprehensive structure that guides agent behavior across single-agent tasks, group chats, pipelines, and swarm simulations.

## Capabilities
*   **System Prompt Generation:** Creates complete system prompts following industry best practices for multi-agent systems.
*   **Structure Enforcement:** Guarantees the inclusion of mandatory sections: Identity (WHO), Capabilities (WHAT), Boundaries (WHAT NOT), Output Format (HOW), Orchestration Context (WHEN), and Termination (STOP).
*   **Behavioral Refinement:** Improves existing prompts by tightening scope creep, reducing hallucination risk, and clarifying inter-agent roles.

## Example Use Cases
1. **Designing a Research Team:** You can provide the roles for three agents (Data Gatherer, Analyst, Reporter) and ask this agent to write the cohesive system prompt that dictates how they interact within a group chat setting.
2. **Improving Agent Scope:** If an existing agent is too broad or prone to hallucination, feed its current prompt here and request it be hardened with explicit 'Limitations' sections.
3. **Defining Workflow Steps:** For complex pipelines, use this agent to write the context-setting instructions that tell each sequential agent exactly when they should pass control or data to the next step.