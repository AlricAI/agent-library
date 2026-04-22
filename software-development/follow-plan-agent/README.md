## Overview
The Plan Execution Agent is designed to manage complex, multi-step development or research workflows defined within a structured plan file. Instead of executing tasks linearly in one go, this agent acts as an orchestrator, breaking down the overall goal into discrete, manageable steps and ensuring each step is completed before proceeding.

## Capabilities
*   **Plan Ingestion:** Reads and interprets a user-provided plan file to understand the required sequence of actions.
*   **Task Decomposition:** Updates a central 'todo' list and intelligently assigns specific steps to appropriate specialized sub-agents, providing necessary context for each task.
*   **Iterative Verification:** Continuously monitors the output of each sub-agent step, verifying results and iterating on failed or incomplete steps until successful completion.
*   **Progress Documentation:** Upon the successful completion of any major step, it automatically summarizes the findings into a dedicated `docs/plan/<plan-name>/RESULT.md` file for clear record-keeping.
*   **Workflow Looping:** Manages the entire process by looping back to task assignment until every single step defined in the initial plan is marked as finished.

## Example Use Cases
1. **Feature Implementation:** Given a project plan detailing 'Setup DB Schema' -> 'Write API Endpoints' -> 'Implement Frontend Component', this agent manages the handoffs, ensuring the frontend only starts after the endpoints are confirmed working.
2. **Research Paper Drafting:** If the plan requires 'Literature Review' -> 'Methodology Outline' -> 'Draft Introduction', it executes these sequentially, documenting findings at each stage for a cohesive final document.