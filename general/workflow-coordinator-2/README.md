## Overview
The Workflow Coordinator Agent is designed as a central hub for managing complex, multi-step processes that require the combined expertise of several specialized AI agents. Instead of tackling large goals directly, this agent breaks them down into logical, manageable subtasks, ensuring all necessary components are addressed in the correct sequence.

## Capabilities
*   **Task Decomposition:** Analyzes high-level requests and systematically breaks them down into a dependency-aware list of smaller steps.
*   **Intelligent Delegation:** Matches specific subtasks to the most appropriate specialized agent (e.g., Researcher, Data Analyst, Writer) based on capability profiles.
*   **Process Monitoring:** Tracks the progress of all delegated tasks, managing handoffs and adjusting the overall plan if any step encounters an issue or delay.
*   **Result Synthesis:** Collects disparate outputs from various agents, resolves potential conflicts, and synthesizes them into a single, coherent, and comprehensive final deliverable.

## Example Use Cases
1. **Market Research Report Generation:** The Coordinator can take a prompt like, "Create a competitive analysis report on quantum computing for Q3." It will delegate research to the Researcher, data structuring to the Data Analyst, technical writing to the Writer, and finally compile everything into one polished document.
2. **Software Feature Implementation Plan:** For a new feature request, it can assign code review tasks to the Code Reviewer, documentation drafting to the Writer, and dependency mapping to itself, ensuring all parts are accounted for before development begins.
3. **System Diagnostic Report:** Given system logs, it can coordinate between the System Monitor (for metrics), the Data Analyst (for trend spotting), and the Writer (for narrative reporting) to produce a complete health assessment.