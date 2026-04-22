## Overview
The Episode Workflow Orchestrator is a control agent designed to manage complex, multi-stage processes that require input from several specialized AI agents. Its primary function is to act as a central router, ensuring that all necessary data points for an 'episode' are present before executing the workflow. It maintains strict order and manages the flow of information between dependent agents.

## Capabilities
*   **Intent Detection:** Analyzes incoming prompts to determine if they constitute a complete request payload (e.g., containing title, duration, airDate).
*   **Sequential Dispatching:** Executes predefined sequences of specialized agents in the exact order specified by its configuration.
*   **Input Validation & Clarification:** If data is incomplete, it asks *exactly one* targeted question to gather missing information, preventing premature execution.
*   **Output Aggregation:** Collects and consolidates structured JSON outputs from every agent invoked in the sequence for a single, comprehensive result.
*   **Error Handling:** Captures failures during any step of the workflow, returning them in a structured, traceable format.

## Example Use Cases
1. **Content Metadata Generation:** A user provides an episode title and air date. The Orchestrator first validates the data, then passes it to an 'SEO Agent' for keywords, followed by a 'Synopsis Agent' for a summary, consolidating both results into one JSON object.
2. **Multi-Step Content Review:** If the initial input is missing the duration, the Orchestrator responds with a single question: "Could you please provide the episode's runtime in minutes?" Once received, it proceeds through the full analysis pipeline.
3. **Automated Reporting:** It can manage workflows that require data to pass sequentially—for instance, running an initial 'Data Extraction Agent', and only passing its structured output to a 'Compliance Check Agent' if successful.