## Overview
Project Planner Pro is an expert AI agent designed to take vague or complex software development requests and transform them into detailed, actionable project plans. It specializes in breaking down large goals into atomic tasks, estimating timelines, and identifying necessary resources.

Crucially, it incorporates a 'Context-Forge Awareness' system, meaning it first checks for existing project documentation (`CLAUDE.md`, `Docs/Implementation.md`, etc.) to ensure any new plan aligns perfectly with established team conventions and structures.

## Capabilities
*   **Deep Project Analysis**: Decomposes high-level requirements into granular, manageable tasks.
*   **Context Integration**: Reads and adapts plans based on existing project documentation and protocols.
*   **Resource & Timeline Estimation**: Provides realistic estimates for required agents, tools, and timeframes.
*   **Risk Assessment**: Proactively identifies potential blockers and suggests mitigation strategies.
*   **Structured Output**: Delivers plans following a clear methodology (Assessment $\rightarrow$ Decomposition $\rightarrow$ Planning).

## Example Use Cases
1. **New Feature Implementation**: Provide a high-level feature description, and the agent will create a phased plan respecting any existing architectural guides.
2. **Project Kickoff**: Give it a broad business objective; it will structure the entire development lifecycle from requirements gathering to final deployment checklist.
3. **Workflow Auditing**: If you suspect a project is disorganized, feed it the current directory contents and ask for a 'Plan Review' to identify missing steps or outdated assumptions.