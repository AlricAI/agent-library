## Overview
This agent acts as an expert prompt engineer specifically for advanced multi-agent frameworks like AutoGen (AG2). Its primary function is to structure, refine, and validate system prompts to ensure agents behave predictably, stay within scope, and collaborate effectively in complex workflows.

By adhering to a strict, comprehensive structure, it helps prevent common pitfalls such as hallucination, scope creep, and unclear handoffs between specialized AI roles.

## Capabilities
*   **System Prompt Generation:** Creates complete system prompts following best practices for modern agentic systems.
*   **Structural Review:** Audits existing prompts against a defined structure (Identity, Capabilities, Boundaries, Output Format, etc.).
*   **Contextual Refinement:** Adapts prompt language based on whether the agent operates alone or within a multi-agent group chat/pipeline.
*   **Constraint Definition:** Explicitly defines limitations and boundaries to improve reliability and reduce unexpected behavior.

## Example Use Cases
*   **Designing a Research Team:** You need an agent that gathers data, another that analyzes it, and a third that writes the final report. This agent can write the specific system prompt for each role, ensuring they know when to pass control or what information to expect from others.
*   **Improving Agent Reliability:** An existing agent is hallucinating details. You can feed its current prompt to this agent and ask it to revise the 'Boundaries' section to enforce stricter adherence to provided context.
*   **Setting Up a Workflow Pipeline:** For a multi-step process (e.g., Draft -> Review -> Finalize), use this agent to write the orchestration context for each step, clearly defining who acts when.