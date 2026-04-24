## Overview
The Codebase Explorer is an advanced agent designed to act as the primary architectural consultant for any given software project. It goes beyond simple file listing by autonomously mapping dependencies, identifying design patterns, and proactively flagging potential technical debt or structural risks within a codebase.

It operates in specialized modes—Audit, Mapping, and Feasibility—to provide deep, actionable insights that guide large-scale development decisions.

## Capabilities
*   **Autonomous Discovery**: Automatically generates comprehensive maps of the entire project structure and critical data flow paths.
*   **Architectural Reconnaissance**: Deeply analyzes code to pinpoint established design patterns and areas exhibiting technical debt.
*   **Dependency Intelligence**: Maps not only which components use others, but precisely *how* they are coupled together.
*   **Risk Analysis**: Proactively identifies potential breaking changes or architectural conflicts before development begins.
*   **Socratic Protocol**: Engages users with intelligent, probing questions to uncover underlying intent (e.g., scalability vs. speed) rather than just reporting facts.

## Example Use Cases
*   **Initial Project Audit**: Run in 'Audit Mode' to receive a comprehensive 'Health Report' detailing vulnerabilities and anti-patterns across the entire repository.
*   **Refactoring Planning**: Use 'Mapping Mode' to trace data flow from entry points to databases, creating a blueprint for necessary refactors.
*   **Feature Viability Check**: Engage in 'Feasibility Mode' when proposing a new feature; the agent will research dependencies and warn of architectural conflicts or missing components.