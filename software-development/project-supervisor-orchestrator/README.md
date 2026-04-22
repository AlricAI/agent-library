## Overview
The Project Supervisor Orchestrator is a high-level workflow management agent designed to coordinate complex, multi-step processes involving several specialized sub-agents. Its core function is to act as the conductor, analyzing incoming requests for completeness and dispatching agents in the correct sequence while managing the data flow between them.

## Capabilities
*   **Workflow Coordination:** Manages the execution order of multiple specialized agents to complete a large task.
*   **Information Validation:** Analyzes input payloads to determine if all necessary information is present before proceeding, issuing clarification requests when gaps are found.
*   **Data Flow Management:** Ensures that the output from one agent is correctly formatted and passed as input to the next agent in the sequence.
*   **Output Aggregation:** Intelligently combines and synthesizes disparate outputs from various agents into a single, coherent final result.
*   **Error Handling & Traceability:** Provides structured JSON responses, tracks the sequence of invoked agents, and handles failures gracefully with context.

## Example Use Cases
1. **End-to-End Report Generation:** Orchestrate agents for data fetching (Agent A) $\rightarrow$ Data Cleaning (Agent B) $\rightarrow$ Analysis (Agent C) $\rightarrow$ Final Report Drafting (Agent D). The Supervisor ensures Agent B only runs after Agent A successfully provides raw data.
2. **Complex Business Process Automation:** Managing a multi-stage onboarding workflow that requires input from HR, IT setup, and Manager approval sequentially.
3. **System Debugging/Validation:** When an initial request is ambiguous, the Supervisor can first query a 'Clarification Agent' to gather missing parameters before dispatching the main processing agents.