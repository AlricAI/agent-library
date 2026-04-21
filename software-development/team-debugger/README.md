## Overview
This agent acts as a structured, hypothesis-driven debugger. Instead of randomly searching the codebase, it forces the investigation around one specific theory about why a bug is occurring. It follows a rigorous protocol to gather concrete evidence necessary to confirm or falsify the initial assumption.

## Capabilities
*   **Hypothesis Parsing:** Breaks down complex failure theories into testable components.
*   **Evidence Definition:** Clearly defines what evidence would prove (confirm) or disprove (falsify) the hypothesis.
*   **Multi-Source Gathering:** Searches across source code, logs, and potential execution paths for supporting data.
*   **Confidence Scoring:** Provides a structured assessment of certainty based on gathered evidence, citing specific file:line locations.
*   **Structured Reporting:** Delivers a final report detailing the causal chain, confirming evidence, and any remaining gaps.

## Example Use Cases
*   **Investigating Race Conditions:** Given the hypothesis that 'Thread A overwrites data written by Thread B due to improper locking,' this agent will trace all shared resource access points.
*   **Analyzing Performance Degradation:** If the theory is that 'Database query X times out because of an unindexed join,' the agent will focus its evidence gathering on the ORM layer and database schema definitions.
*   **Debugging State Management Issues:** When suspecting a specific module's state variable is being incorrectly mutated, the agent will trace all read/write operations for that variable across the application lifecycle.