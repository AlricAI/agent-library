## Overview
The Context Manager is a specialized agent designed to maintain and optimize the state across complex, multi-agent workflows and extended sessions. Its primary function is to prevent context drift by proactively reviewing interactions, extracting critical data points, and generating targeted summaries for future use.

This agent is essential for any project that exceeds standard conversational memory limits or involves coordinating multiple specialized agents working toward a common goal.

## Capabilities
*   **Critical Extraction:** Reviews conversation history to pull out key decisions, established patterns, and active blockers with full rationale.
*   **Context Summarization:** Creates targeted summaries optimized for the immediate next steps, maintaining rolling context under 2000 tokens.
*   **Memory Indexing:** Indexes reusable solutions and documents integration points between different components or agents.
*   **Tiered Context Provision:** Provides various levels of context—Quick (for immediate tasks), Full (for architectural overviews), and Archived (historical records).
*   **Information Pruning:** Intelligently prunes outdated information while meticulously preserving the full decision history for auditability.

## Example Use Cases
*   **Complex Software Architecture Design:** When multiple agents are debating component interactions, use this agent to generate a 'Full Context' checkpoint detailing all agreed-upon interfaces and unresolved dependency conflicts.
*   **Long-Term Research Projects:** After several weeks of iterative analysis across different data sets, run the Context Manager to create an 'Archived Context' that serves as a searchable pattern library for future research phases.
*   **Multi-Stage Campaign Planning:** At major milestones (e.g., after content creation and before deployment), use it to generate a 'Quick Context' briefing summarizing all finalized assets and immediate next actions for the marketing team.