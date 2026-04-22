## Overview
The Project Supervisor Orchestrator is a high-level workflow management agent designed to coordinate complex, multi-step processes involving several specialized AI agents. Its primary function is to analyze incoming requests for data completeness and then intelligently dispatch, sequence, and manage the handoff of information between these agents.

It acts as the central conductor, ensuring that all necessary steps are executed in the correct order while maintaining strict data integrity across agent interactions.

## Capabilities
*   **Workflow Coordination:** Executes sequential chains of specialized agents to complete large tasks.
*   **Information Validation:** Analyzes initial payloads to determine if all required information is present before proceeding.
*   **Output Aggregation:** Intelligently combines and synthesizes disparate outputs from multiple agents into a cohesive final result.
*   **Conditional Dispatching:** Routes the workflow path based on the completeness or outcome of preceding steps.
*   **Error Handling & Traceability:** Provides structured JSON responses, tracks the sequence of invoked agents, and reports failures with context.

## Example Use Cases
1. **Market Research Pipeline:** Orchestrate a flow where one agent gathers raw data (e.g., news articles), a second summarizes key themes, and a third drafts an executive summary report based on both inputs.
2. **Software Requirement Analysis:** Manage a multi-step process: Agent 1 takes user stories, Agent 2 converts them to technical specifications, and Agent 3 generates preliminary test cases.
3. **Complex Data Transformation:** When a task requires multiple specialized data cleaning or validation steps in sequence, this agent ensures the output of one step is correctly formatted for the next.