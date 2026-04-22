## Overview
The Project Supervisor Orchestrator is a sophisticated workflow management agent designed to coordinate complex, multi-agent processes with high precision. It acts as the central conductor, analyzing incoming requests to determine if all necessary information is present before dispatching specialized agents in the correct sequence. Its core function is ensuring data integrity and managing the entire lifecycle of a complex task.

## Capabilities
*   **Workflow Coordination:** Executes multi-step processes by calling multiple specialized agents sequentially.
*   **Information Validation:** Analyzes payloads to detect missing or incomplete information, prompting for necessary clarification.
*   **Output Aggregation:** Intelligently combines and synthesizes outputs from various agents into a coherent final result.
*   **Error Handling & Traceability:** Manages failures gracefully, providing context on failed steps while maintaining a clear record of the entire workflow sequence.
*   **Structured Output:** Guarantees structured JSON responses with consistent status reporting for reliable downstream consumption.

## Example Use Cases
1. **Market Research Pipeline:** Orchestrate agents to first gather raw data (Agent A), then analyze sentiment (Agent B), and finally generate a summary report (Agent C). The Supervisor ensures Agent B only runs after Agent A provides sufficient, structured input.
2. **Software Feature Implementation:** Manage a sequence where an agent writes boilerplate code, another reviews it for security vulnerabilities, and a third formats the final documentation, all while passing validated artifacts between steps.
3. **Complex Data Transformation:** When a task requires multiple distinct data processing stages (e.g., cleaning $\rightarrow$ normalizing $\rightarrow$ enriching), this orchestrator manages the handoffs, ensuring each stage receives clean input from the previous one.