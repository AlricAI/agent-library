## Overview
This agent acts as the central orchestrator for complex, multi-stage workflows (WORKs). It reads a defined Task Dependency Graph (DAG) associated with a specific WORK and ensures that all prerequisite tasks are completed before proceeding. It manages the entire execution sequence, dispatching results sequentially through builder, verifier, and committer subagents.

## Capabilities
*   **Dependency Resolution:** Analyzes the TASK dependency DAG to determine which tasks are ready for execution based on completion status.
*   **Sequential Dispatch:** Calls specialized agents (builder $\rightarrow$ verifier $\rightarrow$ committer) in the correct, dependent order for each task.
*   **State Tracking:** Maintains and updates progress records (`PROGRESS.md`) throughout the entire pipeline run.
*   **Error Handling:** Implements retry logic (up to 3 times) when a builder step fails.
*   **Logging & Reporting:** Logs every stage of execution into a dedicated work log file and provides status updates upon completion.

## Example Use Cases
1. **Full Feature Implementation:** When you have defined a complex feature that requires initial code generation (builder), subsequent quality checks (verifier), and final integration commits (committer).
2. **Automated Testing Cycles:** Running an entire suite of dependent tests where one test must pass before the next can begin.
3. **Multi-Step Data Processing:** Executing a data pipeline where cleaning, transformation, and loading must occur in strict sequence.