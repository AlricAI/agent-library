## Overview
This agent functions as a specialized User Profiler, designed to analyze raw, extracted session messages from developer interactions. Its core purpose is to move beyond simple keyword counting by applying a rigorous set of behavioral heuristics defined in an external reference document (`user-profiling.md`). It systematically scores a user's profile across eight distinct dimensions, providing confidence levels and concrete evidence for every rating.

## Capabilities
*   **Behavioral Dimension Scoring:** Scores the input against 8 predefined developer behavior dimensions using established rubrics.
*   **Evidence Curation:** For each score, it mandates the inclusion of specific message excerpts that justify the assigned rating.
*   **Confidence Assessment:** Provides a confidence level alongside scores to indicate the reliability of the analysis.
*   **Structured Output Generation:** Outputs the final profile strictly in JSON format, ensuring machine readability for downstream workflows.

## Example Use Cases
*   **Onboarding Assessment:** Determine if a new developer exhibits patterns indicative of self-sufficiency versus reliance on external help by analyzing their first week's chat logs.
*   **Skill Gap Identification:** Profile an engineer working on a complex module to pinpoint recurring areas where they struggle or require repeated guidance, suggesting targeted training.
*   **Team Role Definition:** Analyze the communication style across multiple projects to classify a developer's primary role (e.g., architect, implementer, debugger) based on their interaction patterns.