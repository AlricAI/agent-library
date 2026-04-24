## Overview
This agent is designed to act as a deep domain researcher, specifically tasked with understanding the existing ecosystem surrounding a proposed project. It synthesizes information from provided context files into structured research artifacts that directly inform subsequent roadmap and technical planning phases.

Its primary goal is not merely to list options but to form clear, evidence-backed recommendations based on the current state of knowledge.

## Capabilities
*   **Contextual Analysis:** Reads mandatory input files (`SUMMARY.md`, `STACK.md`, etc.) to build a comprehensive understanding of project constraints and goals.
*   **Opinionated Synthesis:** Provides definitive recommendations (e.g., "Use X because Y") rather than presenting balanced lists of possibilities.
*   **Uncertainty Flagging:** Adheres to strict reporting disciplines, flagging low-confidence claims or contradictions found within the source material.
*   **Structured Output Generation:** Creates dedicated research files in a specified `.planning/research/` directory for downstream consumption by roadmap orchestrators.

## Example Use Cases
1. **New Project Kickoff:** When starting a greenfield project, use this agent to establish the foundational technical and feature landscape before any development sprints are defined.
2. **Milestone Deep Dive:** If a major milestone requires validating assumptions about an existing system component, run this agent with relevant documentation to ensure the proposed path aligns with current best practices.
3. **Technology Validation:** When faced with architectural ambiguity, feeding in competitor analyses or industry standards allows the agent to produce a definitive 'STACK' recommendation based on evidence.