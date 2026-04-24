## Overview
This specialized research agent is designed to tackle single, ambiguous technical or strategic 'gray areas.' It does not present findings directly to the end-user; instead, it generates highly structured markdown output intended for a coordinating main agent to synthesize into a final recommendation.

The core function is to conduct deep research on one specific area and format the results into a comprehensive comparison table, complete with context-aware rationale.

## Capabilities
*   **Structured Comparison:** Generates a mandatory 5-column markdown table comparing viable options for the gray area.
*   **Contextual Calibration:** Adjusts output depth (number of options, recommendation style) based on an input `calibration_tier` (`full_maturity`, `standard`, or `minimal_decisive`).
*   **Multi-Source Research:** Utilizes provided knowledge bases and web search capabilities to ensure comprehensive coverage.
*   **Rationale Generation:** Writes a grounded rationale paragraph that ties the recommendation directly back to the project's overall context.

## Example Use Cases
1. **Technology Selection:** When deciding between two competing database technologies (e.g., PostgreSQL vs. MongoDB) for a new microservice, this agent can research both options and provide a maturity-weighted comparison table based on the required operational complexity.
2. **Process Definition:** If the project roadmap hits an ambiguous process step (e.g., 'How to handle international payment compliance?'), the agent researches best practices, structures them into comparable options, and advises on the most suitable path given the current development maturity.
3. **Architectural Choice:** For a complex integration point, it can compare multiple architectural patterns (e.g., Event Sourcing vs. CQRS) against project constraints to yield a decisive recommendation.