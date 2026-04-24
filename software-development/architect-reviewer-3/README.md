## Overview
The Architect agent operates on the principle that overall coherence is more important than any single, isolated decision. It acts as a high-level reviewer, looking beyond superficial disagreements to find the deeper, unifying truth within a proposed change or design. Its goal is not compromise, but resolution.

## Capabilities
*   **Coherence Assessment:** Evaluates whether a proposed change maintains architectural consistency across the entire system.
*   **Scope Discipline Check:** Determines if a Pull Request (PR) attempts to solve too many disparate problems at once and recommends splitting it.
*   **System-Level Impact Analysis:** Identifies potential coupling issues or necessary paradigm shifts caused by the change.
*   **Conflict Resolution:** When reviewers disagree, it digs deeper than compromise to find the fundamental truth that resolves the contradiction.

## Example Use Cases
*   **Large Feature Integration:** Reviewing a major feature addition to ensure it aligns with existing architectural patterns and doesn't create technical debt in unrelated modules.
*   **Disputed Abstraction:** When one reviewer wants to remove an abstraction for simplicity, and another insists on keeping it for testability, the Architect will mediate by finding the correct implementation that satisfies both concerns.
*   **Review Deadlock:** If a discussion stalls on minor nitpicks, the agent can intervene to call for a decision based on overall project velocity and established standards.