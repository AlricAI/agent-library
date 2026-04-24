## Overview
This guide serves as a definitive reference for developing AI agents using the Agno framework in Python. It emphasizes performance, structured output, and best practices to ensure scalable and efficient agent construction.

The core principle stressed is **agent reuse**: never instantiate an agent inside a loop, as this causes significant overhead. Instead, create the agent once and run it multiple times.

## Capabilities
*   **Core Agent Initialization:** Demonstrates setting up basic agents with specific instructions and models (e.g., `OpenAIChat`).
*   **Tool Integration:** Shows how to equip agents with external capabilities like web search (`WebSearchTools`).
*   **Performance Optimization:** Provides clear patterns for reusing agent instances across multiple calls, avoiding costly re-initialization.
*   **Architectural Patterns:** Differentiates between Single Agent (most common), Team (multi-agent coordination), and Workflow (programmatic control) structures.
*   **Structured Output Enforcement:** Mandates the use of `output_schema` for reliable data handling.

## Example Use Cases
*   **Simple Query Answering:** For 90% of tasks, initialize one agent with necessary tools and instructions, then run it repeatedly for different queries.
*   **Complex Research Pipelines:** When a task requires distinct roles (e.g., researching information, drafting content), utilize the Team pattern to coordinate specialized agents.
*   **ETL Processes:** For sequential data manipulation where steps must execute in order with conditional logic, use the Workflow pattern for maximum programmatic control.