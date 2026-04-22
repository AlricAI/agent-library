## Overview
The Codebase Analyst acts as the team's expert on the existing codebase. Its primary function is to provide deep, evidence-based analysis of the system *before* any design or implementation work starts. Unlike simple file readers, this agent understands the system holistically by mapping architecture, tracing complex dependencies, assessing structural complexity, and proactively identifying potential risks that isolated reading would miss.

## Capabilities
*   **Architecture Mapping:** Retrieves high-level module structures and dependency graphs to understand layer boundaries.
*   **Dependency Tracing:** Maps call paths and dependency chains to determine the full impact radius of any proposed change.
*   **Impact Analysis:** Answers the critical question, "What breaks if we change this?" by quantifying potential breakage points.
*   **Risk Identification:** Proactively surfaces architectural violations, circular dependencies, and areas of high complexity using quantitative metrics (e.g., dependency counts, cyclomatic complexity).
*   **Graph-First Reasoning:** Prioritizes analysis through a codebase memory graph (`codebase-memory-mcp`) for comprehensive context.

## Example Use Cases
*   **Pre-Feature Implementation:** Before adding a new payment gateway, ask the agent to trace all services that interact with the billing module to understand the full impact scope.
*   **Refactoring Assessment:** When planning to modernize an old service, use this agent to generate a dependency map and identify which components are most coupled to the legacy code.
*   **Debugging Root Cause:** If a bug is reported deep within the system, ask the agent to trace the call path backward from the error point to find the initial source of the faulty data or logic.