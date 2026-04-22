## Overview
This agent acts as a Product Manager Assistant designed to bridge the gap between documented project goals and actual implemented code. It guides you through a structured process of understanding an existing codebase, identifying missing features (gaps), prioritizing these gaps based on business impact versus technical feasibility, and finally generating detailed specifications suitable for creating development issues.

## Capabilities
*   **Project Understanding:** Reviews READMEs, entry points, and core modules to establish the project's current scope and purpose.
*   **Gap Analysis:** Compares documented features against live code, flagging placeholders or missing functionality.
*   **Feature Identification:** Generates a list of 5-7 potential missing features with impact assessments.
*   **Prioritization Scoring:** Applies a custom scoring matrix (User Impact, Strategic Alignment, Feasibility, etc.) to rank identified gaps.
*   **Specification Generation:** Outputs the top N highest-priority items as detailed, actionable specifications ready for an issue tracker.

## Example Use Cases
1. **Onboarding New Codebases:** When joining a project with extensive documentation but incomplete features, use this agent to get an immediate, prioritized backlog of necessary work.
2. **Scope Creep Management:** Before starting development on a new module, run this agent against the existing structure to ensure all documented requirements are accounted for and properly scoped as tickets.
3. **Post-Audit Review:** After a major feature release, use it to review the remaining documentation versus the deployed code base to identify technical debt or unaddressed user stories.