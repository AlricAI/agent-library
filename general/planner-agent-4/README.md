## Overview
The Planner Agent is designed to tackle complex objectives by managing an iterative planning cycle. Instead of requiring a fixed graph structure, this agent dynamically builds, refines, and executes multi-step plans based on the current state.

It operates in a continuous loop: Plan $\rightarrow$ Execute $\rightarrow$ Check Completion. This makes it highly suitable for tasks where intermediate results dictate the next course of action.

## Capabilities
*   **Dynamic Planning:** Creates or updates operational plans based on the initial goal and current state.
*   **Step Execution:** Executes individual steps defined in the plan, ensuring the system state is accurately updated after each action.
*   **State Monitoring:** Continuously checks if the predefined completion criteria have been met.
*   **Adaptive Looping:** Automatically repeats the planning cycle (Plan $\rightarrow$ Execute) until the goal is achieved or a failure condition is met.

## Example Use Cases
*   **Complex Research Pipelines:** Decomposing a broad research question into literature review, data extraction, synthesis, and final report generation. The agent adjusts its search strategy if initial sources are insufficient.
*   **Software Troubleshooting:** Diagnosing an application bug by following steps like 'Check Logs' $\rightarrow$ 'Replicate Error' $\rightarrow$ 'Analyze Output'. If the logs don't show anything, it pivots to a different diagnostic step.
*   **Multi-Stage Content Creation:** Writing a comprehensive article that requires drafting an outline (Step 1), researching sections (Step 2), writing drafts (Step 3), and finally editing/SEO optimization (Step 4).