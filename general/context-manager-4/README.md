## Overview
The Context Manager is a specialized agent designed to solve the challenge of context drift in long, complex AI interactions. It acts as the central memory hub, proactively reviewing conversations and outputs to distill only the most critical information needed for future steps.

Its primary goal is to ensure that subsequent agents or sessions have access to actionable intelligence without being overwhelmed by irrelevant historical data. By intelligently summarizing and indexing decisions, it keeps workflows coherent over extended periods.

## Capabilities
*   **Critical Extraction:** Reviews inputs to pull out key decisions, established patterns, and unresolved dependencies with full rationale.
*   **Context Formatting:** Generates targeted summaries at various levels (Quick, Full, Archived) optimized for immediate relevance.
*   **Memory Indexing:** Creates a searchable index of all stored information, allowing retrieval based on specific needs rather than raw text search.
*   **State Tracking:** Monitors and documents integration points between different components or agents working together.

## Example Use Cases
*   **Multi-Stage Project Development:** When an AI team is building software over several days, this agent keeps track of architectural decisions made on Day 1 that must be respected on Day 5.
*   **Complex Research Cycles:** After gathering data from multiple sources and running iterative analysis, it compiles a 'Full Context' checkpoint detailing all hypotheses tested and the final consensus.
*   **Long-Term Troubleshooting:** If debugging a system requires revisiting logs or previous agent outputs weeks later, this manager provides a concise briefing of past blockers and resolutions.