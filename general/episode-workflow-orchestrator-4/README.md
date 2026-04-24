## Overview
The Episode Workflow Orchestrator is designed to manage complex, multi-stage tasks that require the coordinated effort of several specialized AI agents. Instead of calling one agent for everything, this orchestrator analyzes an incoming request to determine if all necessary data (the 'episode payload') is present. If it is, it executes a predefined sequence of agents in strict order, passing the output of one step as the input context for the next.

If the initial information is incomplete or ambiguous, the agent will pause and ask exactly one targeted clarifying question to gather the missing details before attempting any execution.

## Capabilities
*   **Intent Detection:** Analyzes incoming prompts to determine if they represent a complete 'episode' workflow request.
*   **Sequential Execution:** Invokes configured agents in a precise, defined order, ensuring data flows correctly between steps.
*   **Payload Validation:** Checks for the presence of all required structured fields (e.g., title, duration, airDate) before proceeding.
*   **Structured Output Generation:** Provides consolidated JSON responses containing outputs from *all* invoked agents, along with clear status indicators and traceability logs.
*   **Error Handling:** Captures agent invocation failures in a structured JSON format for easy debugging.

## Example Use Cases
1. **Content Analysis Pipeline:** You need to analyze a newly recorded episode. The orchestrator first passes the raw transcript to an 'Audio Transcription Agent,' then passes the resulting text to a 'Sentiment Analysis Agent,' and finally sends the sentiment score to a 'Tag Generation Agent' for final output.
2. **Data Enrichment Workflow:** Given a basic event title, you need to enrich it by first querying a 'Historical Data Agent' for context, then passing that context to a 'Market Trend Agent' to predict impact, all within one call.
3. **Guided Intake Forms:** When onboarding a new project, the system detects missing fields (like budget or stakeholder list) and prompts the user with a single question: "Could you please provide the primary stakeholder contact email?" until all necessary data is collected.