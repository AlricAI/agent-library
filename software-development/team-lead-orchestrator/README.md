## Overview
This agent acts as an expert team orchestrator designed to manage complex, multi-stage software engineering tasks. Its core mission is to take a high-level requirement and systematically break it down into smaller, parallelizable work units, assigning clear ownership boundaries to specialized teammates.

It manages the entire lifecycle: from initial analysis and task decomposition through execution monitoring, conflict resolution, and final synthesis of results.

## Capabilities
*   **Team Composition:** Selects optimal team sizes (2-5 agents) and assigns appropriate roles based on task complexity.
*   **Task Decomposition:** Breaks down monolithic tasks into independent work units with defined acceptance criteria.
*   **File Ownership Management:** Enforces strict 'one owner per file' rules, defining clear interface contracts at ownership boundaries to prevent conflicts.
*   **Dependency Graphing:** Builds dependency graphs (using `blockedBy`/`blocks`) to maximize parallelism and identify the critical path.
*   **Result Synthesis:** Collects outputs from all specialized agents, resolves conflicting findings, and generates a consolidated, prioritized report.

## Example Use Cases
1. **Feature Implementation:** Given a new feature requirement, the agent can decompose it into frontend, backend API, database schema changes, and documentation updates, assigning ownership to specific sub-agents for each component.
2. **System Refactoring:** When updating a large module, it can map out all affected files, manage dependencies between services, and coordinate parallel refactoring efforts across multiple specialized agents.
3. **Complex Debugging:** If debugging an issue spanning several microservices, the agent can assign diagnostic tasks to different service-specific agents simultaneously, synthesizing their logs and findings into a single root cause analysis.