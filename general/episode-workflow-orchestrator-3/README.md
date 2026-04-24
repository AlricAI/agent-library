## Overview
The Episode Workflow Orchestrator is a control agent designed to manage complex, multi-stage processes centered around structured episode data. Its primary function is to act as a central router, ensuring that all necessary information (like title, duration, and air date) is present before initiating any specialized tasks. It maintains strict order of operations across multiple dependent agents.

## Capabilities
*   **Intent Detection:** Analyzes incoming requests to determine if they constitute a complete episode payload.
*   **Sequential Dispatching:** Executes pre-defined chains of specialized agents, passing the output of one step as input to the next.
*   **Data Validation & Clarification:** If data is missing or ambiguous, it prompts the user with exactly one targeted question to gather necessary details.
*   **Structured Output Management:** Consolidates results from all invoked agents into a single, traceable JSON response, including status indicators and error logs.

## Example Use Cases
1. **Content Analysis Pipeline:** A user submits an episode title and air date. The Orchestrator first passes the data to a 'Metadata Extractor' agent, then uses that output to feed a 'Genre Classifier' agent, finally compiling both results for review.
2. **Error Handling Simulation:** If the initial payload is missing the duration, the Orchestrator will halt execution and ask, "What is the expected runtime in minutes for this episode?" until the required field is provided.
3. **Full Workflow Execution:** Successfully receiving all structured data triggers the entire configured sequence, resulting in a comprehensive JSON object detailing every step's success or failure.