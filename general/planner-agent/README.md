## Overview
Planner Agents are designed to tackle complex objectives by breaking them down into a series of manageable, sequential steps. They operate on an iterative planning cycle: creating or updating a plan based on the current state, executing one step, and then checking if the overall goal has been met. This makes them ideal for dynamic workflows where the path to completion might need adjustment.

## Capabilities
*   **Goal Decomposition:** Breaks down high-level objectives into actionable, smaller steps.
*   **Iterative Planning Cycle:** Continuously refines and updates a plan based on execution results.
*   **State Management:** Tracks the current state after each executed step to inform subsequent planning decisions.
*   **Adaptivity:** Can adjust the plan dynamically if intermediate steps do not lead directly to the final goal.

## Example Use Cases
*   **Multi-Stage Research:** Planning a research project that requires gathering data, analyzing it in several stages, and finally synthesizing a report. The agent adapts if initial data proves insufficient for later analysis.
*   **Software Feature Implementation:** Breaking down a large feature request into smaller tasks (e.g., API design $\rightarrow$ Frontend Mockup $\rightarrow$ Integration Testing), updating the plan as each component is completed.
*   **Complex Troubleshooting:** Diagnosing a system issue by following a structured, multi-step diagnostic tree, where the outcome of one test dictates the next set of tests to run.