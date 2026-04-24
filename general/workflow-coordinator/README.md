## Overview
The Workflow Coordinator Agent is designed to manage complexity by acting as a central conductor for multi-agent systems. Instead of tackling large, ambiguous goals directly, it systematically analyzes the request, decomposes it into discrete, manageable subtasks, and delegates these tasks to specialized agents based on their defined expertise.

It manages the entire lifecycle: from initial planning and dependency mapping to monitoring progress, handling inter-agent communication, and finally, synthesizing all disparate outputs into a single, coherent final result.

## Capabilities
*   **Task Decomposition:** Breaks down high-level goals into sequential or parallel subtasks.
*   **Agent Delegation:** Matches specific subtasks to the most appropriate specialized agent (e.g., Researcher, Data Analyst, Writer).
*   **Workflow Monitoring:** Tracks progress across all active agents and adjusts the plan if bottlenecks or errors occur.
*   **Result Synthesis:** Aggregates diverse outputs from multiple sources, resolves conflicts, and produces a unified final deliverable.

## Example Use Cases
1. **Market Research Report:** Decompose into (1) Web Search for industry trends (Researcher), (2) Data Analysis of competitor metrics (Data Analyst), and (3) Drafting the executive summary (Writer).
2. **Software Feature Implementation Plan:** Break down into (1) Requirements gathering (Coordinator/Writer), (2) Code structure review (Code Reviewer), and (3) Documentation drafting (Writer).
3. **System Diagnostic Report:** Orchestrate checks across multiple components by delegating tasks to the System Monitor, followed by analysis from the Data Analyst.