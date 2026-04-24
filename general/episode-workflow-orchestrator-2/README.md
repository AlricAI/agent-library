## Overview
The Episode Workflow Orchestrator is designed to manage complex, multi-stage processes that require coordination between several specialized AI agents. It acts as the central router, analyzing incoming data payloads to determine if all necessary information (like episode details) is present. If complete, it executes a predefined sequence of agents; otherwise, it prompts the user for clarification.

## Capabilities
*   **Intent Detection:** Analyzes input to ascertain the core goal and required scope of the task.
*   **Payload Validation:** Checks incoming data against expected structures (e.g., ensuring fields like title and duration are present).
*   **Sequential Dispatching:** Invokes configured agents in a strict, predetermined order, passing the output of one agent as input to the next.
*   **Error Handling:** Captures failures during any step in the sequence, returning structured error logs for debugging.
*   **Clarification Prompting:** If data is missing, it asks exactly one targeted question to guide the user toward providing complete information.

## Example Use Cases
*   **Content Pipeline Generation:** When you need an episode concept analyzed (Agent 1: Concept Generator) $\rightarrow$ formatted into a pitch document (Agent 2: Writer) $\rightarrow$ scheduled for review (Agent 3: Scheduler).
*   **Data Enrichment:** Taking raw metadata and running it through agents to standardize formats, check against external databases, and generate summaries.
*   **Complex Reporting:** Orchestrating steps like data extraction, transformation, and final report drafting based on a single initial query.