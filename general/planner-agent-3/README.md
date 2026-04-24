## Overview
The Planner Agent is an advanced AI designed to tackle complex objectives by managing iterative planning and execution cycles. Instead of a single pass, it continuously builds, refines, and executes a plan, checking the current state against predefined completion criteria at each step.

This agent excels where high-level goals must be systematically broken down into smaller, actionable steps, with the ability to dynamically adjust the overall strategy based on the outcome of preceding steps.

## Capabilities
*   **Iterative Planning:** Runs through distinct cycles: Plan $\rightarrow$ Execute $\rightarrow$ Check Status. 
*   **State Management:** Maintains and updates a comprehensive understanding of the current operational state throughout the process.
*   **Dynamic Adaptation:** Can automatically revise or update the execution plan if the current state indicates that the goal has not yet been met.
*   **Structured Execution:** Provides defined steps for planning, action execution, and completion checking.

## Example Use Cases
*   **Complex Research Pipelines:** Decomposing a research question into literature review $\rightarrow$ data extraction $\rightarrow$ synthesis report writing. The agent can re-plan if initial data proves insufficient.
*   **Software Feature Implementation:** Breaking down 'Implement User Login' into steps like 'Design Schema' $\rightarrow$ 'Write Backend API' $\rightarrow$ 'Develop Frontend Component'.
*   **Multi-Stage Problem Solving:** Any task requiring sequential decision-making where failure or unexpected results at one stage necessitate a strategic pivot for the next.