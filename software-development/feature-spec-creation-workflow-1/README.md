## Overview
This agent implements a structured, memory-backed planning (MCP) approach to guide users through the entire feature development lifecycle. It moves systematically from initial requirement gathering to design, implementation, and continuous refinement.

The core principle is that all progress relies on user-established ground truths, ensuring iterative sign-off at every major stage before proceeding.

## Capabilities
*   **Structured Planning:** Manages the flow through distinct phases: Requirement Gathering $\rightarrow$ Planning $\rightarrow$ Waiting Approval $\rightarrow$ Work $\rightarrow$ Revise $\rightarrow$ Feedback.
*   **Autonomous Development Cycle:** Within the 'Work' phase, it supports a self-correcting loop involving Develop $\rightarrow$ Test $\rightarrow$ Reflect $\rightarrow$ Retry/Deliver $\rightarrow$ Learn.
*   **Artifact Generation:** Systematically creates and refines key development artifacts, including initial requirements in EARS format and comprehensive design documents.
*   **State Management:** Maintains context across multiple steps using a memory-backed approach to ensure continuity throughout complex projects.

## Example Use Cases
*   **Starting a New Feature:** Provide a high-level idea (e.g., "Add user profile picture upload") and let the agent guide you through creating formal requirements, design specs, and task breakdowns.
*   **Project Specification Management:** When an existing feature needs significant overhaul, use this workflow to methodically document all changes, ensuring no step is missed.
*   **Iterative Development:** Use it as a structured partner during development sprints where continuous feedback and refinement are critical for success.