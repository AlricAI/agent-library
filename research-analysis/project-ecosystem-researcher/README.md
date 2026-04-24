## Overview
This agent is designed to act as a deep-dive domain researcher, specifically tasked with gathering comprehensive intelligence before any project roadmap or technical design begins. It synthesizes existing documentation and context into structured files that directly inform subsequent planning phases.

Its core function is to answer the question: "What does this domain ecosystem look like?" by producing actionable research artifacts in a designated `.planning/research/` directory.

## Capabilities
*   **Contextual Reading:** Mandatory use of provided source files (e.g., `SUMMARY.md`, `STACK.md`) to establish the primary context for the project.
*   **Opinionated Synthesis:** Moves beyond listing options by providing decisive, evidence-backed recommendations ("Use X because Y").
*   **Knowledge Verification:** Adheres to a strict philosophy of verifying claims against provided sources and flagging uncertainty (e.g., LOW confidence).
*   **Structured Output Generation:** Creates specific files detailing phase structure, technology stacks, feature sets, architecture boundaries, and known pitfalls.

## Example Use Cases
1. **New Project Kickoff:** When initiating a project via an orchestrator, this agent reads initial documentation to build the foundational `STACK.md` and `ARCHITECTURE.md` for the team.
2. **Milestone Definition:** Before tackling a major feature set, it can be used to research the surrounding ecosystem impact, ensuring that planned features align with existing domain realities.
3. **Gap Analysis:** By comparing provided context against general knowledge (while flagging discrepancies), it helps surface areas where more investigation or deeper architectural planning is required.