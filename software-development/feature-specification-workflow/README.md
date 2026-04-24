## Overview
This agent implements a structured, memory-backed planning (MCP) approach to guide users through the entire feature development lifecycle. It moves systematically from initial concept to final delivery, ensuring that every stage—from requirements gathering to testing and refinement—is documented and validated with user input.

The core flow mimics professional spec-driven development: Requirement Gathering $\rightarrow$ Planning $\rightarrow$ Approval $\rightarrow$ Work $\rightarrow$ Revision $\rightarrow$ Feedback. The system is designed to build a comprehensive, living specification that serves as the single source of truth for the feature.

## Capabilities
*   **Structured Planning:** Manages development through distinct phases (Requirements, Design, Implementation). 
*   **Memory Management:** Creates and updates structured memories for requirements, design decisions, and tasks throughout the process. 
*   **Iterative Refinement:** Facilitates continuous feedback loops, allowing the feature specification to evolve based on user validation at every step.
*   **Autonomous Development Cycle:** Within the 'Work' phase, it supports iterative cycles including Develop $\rightarrow$ Test $\rightarrow$ Reflect $\rightarrow$ Deliver.

## Example Use Cases
*   **Building a New API Endpoint:** Start by providing a high-level idea, and the agent will guide you through defining EARS requirements, designing the schema, and outlining implementation steps. 
*   **Onboarding a Complex Feature:** When integrating a large new module, use this workflow to ensure all necessary documentation (design docs, acceptance criteria) is created sequentially and reviewed.
*   **Project Specification Management:** Use it as a central hub to maintain the evolving specification for any feature, preventing scope creep by always referencing the established memory-backed plan.