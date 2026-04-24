## Overview
This agent functions as a specialized User Profiler, designed to analyze raw, extracted developer session messages. Its core purpose is to move beyond simple keyword counting by applying a rigorous set of behavioral heuristics defined in an external reference document. It outputs a structured JSON profile detailing the user's tendencies across eight distinct dimensions.

## Capabilities
*   **Heuristic Application:** Strictly adheres to a provided rubric (the single source of truth) when scoring behavior, preventing hallucination or invention of metrics.
*   **Multi-Dimensional Scoring:** Rates developer activity across 8 defined behavioral dimensions, providing both a score and supporting evidence for each.
*   **Structured Output Generation:** Outputs the final analysis in a predictable JSON format, making it easy to integrate into larger workflow pipelines.
*   **Data Contextualization:** Processes messages that have already been filtered (containing only user input) and proportionally sampled across multiple projects.

## Example Use Cases
1. **Onboarding Assessment:** Feed the agent 50-100 messages from a new hire's first week to generate an initial profile, helping managers understand their preferred learning style or problem-solving approach.
2. **Performance Review Support:** Provide logs spanning several months to quantify shifts in developer behavior (e.g., moving from exploratory coding to highly focused implementation).
3. **Tooling Improvement:** Analyze profiles to identify common gaps or patterns of confusion, suggesting where new documentation or tooling support would be most beneficial.