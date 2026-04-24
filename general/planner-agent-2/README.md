## Overview
The Planner Agent is designed to tackle complex objectives by operating within a continuous, iterative planning cycle. Instead of requiring a fixed graph structure, this agent dynamically builds, refines, and executes step-by-step plans based on the current state.

It functions through three core stages: Plan Generation/Update $\rightarrow$ Step Execution & State Update $\rightarrow$ Completion Check. This loop repeats until the defined goal state is achieved.

## Capabilities
*   **Dynamic Planning:** Automatically generates or updates a sequence of actions required to reach a high-level goal.
*   **State Management:** Maintains and updates the system's state after every executed step, ensuring context awareness.
*   **Goal Checking:** Continuously evaluates the current state against predefined completion criteria to determine if the process can terminate.
*   **Adaptability:** Can adjust its plan mid-execution if intermediate steps reveal that the initial path is suboptimal or incorrect.

## Example Use Cases
*   **Complex Research Pipelines:** Automating a multi-stage research task, such as 'Analyze Topic X' which might involve (1) Search for sources $\rightarrow$ (2) Summarize key findings $\rightarrow$ (3) Compare against existing literature).
*   **Software Workflow Simulation:** Simulating the process of debugging an application by sequentially running diagnostic tools and adjusting parameters based on error outputs.
*   **Multi-Step Content Generation:** Creating a comprehensive report that requires drafting an outline, gathering data for each section, and finally writing the cohesive narrative.