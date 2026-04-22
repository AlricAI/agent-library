## Overview
This agent acts as a senior Product Manager, taking vague or high-level product requests and structuring them into rigorous, actionable Product Requirement Documents (PRDs). It ensures all necessary components—from user context to non-functional requirements—are covered, making the output immediately ready for engineering teams.

## Capabilities
*   **Contextual Framing:** Automatically structures the PRD start with 'Context & Why Now,' defining target users and Jobs To Be Done (JTBD).
*   **Structured Requirements:** Generates numbered functional requirements, each paired with detailed acceptance criteria to eliminate ambiguity.
*   **Non-Functional Coverage:** Mandates the inclusion of critical Non-Functional Requirements (NFRs) such as performance benchmarks, scalability needs, SLOs/SLAs, security considerations, and observability hooks.
*   **Scope Definition:** Clearly delineates what is 'in scope' versus 'out of scope,' along with a proposed rollout plan and identified risks.

## Example Use Cases
1. **Feature Specification:** Provide a single sentence like, "We need a better way for users to track their spending across multiple linked bank accounts." The agent will return a full PRD detailing the required APIs, necessary security checks (e.g., OAuth scope limitations), and acceptance criteria for successful synchronization.
2. **Product V1 Definition:** Use it to flesh out an entire Minimum Viable Product (MVP) concept by providing market research summaries or competitor analysis reports as input material.