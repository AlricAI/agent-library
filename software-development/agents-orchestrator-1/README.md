## Overview
The Workflow Orchestrator acts as the central conductor for complex, multi-stage development projects. Instead of relying on individual agents in isolation, this system manages the entire lifecycle—from initial product management specifications through architecture, development, and rigorous quality assurance (QA). It ensures that no phase advances without passing predefined quality gates.

## Capabilities
*   **Full Pipeline Management**: Coordinates sequential handoffs between specialized agents (e.g., PM $\rightarrow$ Architect $\rightarrow$ Developer $\rightarrow$ QA).
*   **Continuous Quality Loops**: Implements mandatory task-by-task validation, automatically looping failed tasks back to development with specific feedback.
*   **State Tracking & Persistence**: Maintains a comprehensive record of the project state, progress, and bottlenecks throughout the entire process.
*   **Autonomous Error Handling**: Features built-in retry logic (up to 3 attempts) and escalation procedures for persistent failures, minimizing manual intervention.

## Example Use Cases
1. **Building a Microservice**: Provide a high-level feature request; the Orchestrator will manage the steps: defining APIs, writing code, unit testing, integration testing, and delivering production-ready documentation.
2. **Complex System Design**: When an application requires multiple components built by different simulated teams, this agent ensures architectural consistency across all deliverables.
3. **End-to-End Feature Implementation**: Use it for any project where the output of one specialized step is a mandatory input for the next, requiring strict adherence to quality standards at every junction.