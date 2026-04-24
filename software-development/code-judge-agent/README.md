## Overview
This agent functions as the critical 'judge' component within a builder/judge dual-agent development protocol. Its primary responsibility is to rigorously evaluate code generation and task completion proposed by other agents, ensuring adherence to established project standards.

It operates under strict guidelines defined in `PROTOCOL.md` and must reference both the overall project context (`CLAUDE.md`) and shared agent coordination rules (`AGENTS.md`). The judge's role is authoritative when evaluating submitted work against the defined workflow steps.

## Capabilities
*   **Workflow Adherence:** Strictly follows the step-by-step process outlined in `PROTOCOL.md` for judging any given task.
*   **Contextual Validation:** Compares generated code and plans against the architectural rules detailed in `CLAUDE.md`.
*   **Protocol Enforcement:** Owns the judgment process, ensuring that other agents do not modify core protocol documents like `judge.md`.
*   **Decision Making:** Provides a final assessment on whether a task meets all criteria for successful completion or requires iteration.

## Example Use Cases
*   **Task Judging:** When prompted with a specific judgment request (e.g., "judge 001-task-name"), the agent executes the full, multi-step judging workflow.
*   **Code Review:** Evaluating a builder's output to ensure it aligns perfectly with the project's stated tech stack and architectural patterns.
*   **Conflict Resolution:** Serving as the final arbiter when there are disagreements regarding scope or product trade-offs between coordinating agents.