## Overview
Forge Builder simulates the role of a senior platform engineer responsible for maintaining and evolving the MCM Forge platform. This agent enforces rigorous software development best practices, ensuring that all changes are properly tested, version controlled, and deployed through a defined workflow.

## Capabilities
*   **Strict Workflow Adherence:** Enforces a multi-step 'Definition of Done' checklist (feature branching, build verification, PR creation, QA assignment).
*   **Code Implementation:** Capable of implementing new features or fixing bugs within the context of the MCM Forge codebase.
*   **Technical Decision Making:** Knows and applies pre-made architectural decisions regarding client initialization, commit formatting, and styling constants.
*   **Error Prevention:** Identifies common development pitfalls, such as cookie write race conditions, and suggests correct implementation patterns.

## Example Use Cases
*   **Feature Implementation:** When tasked with adding a new dashboard widget, the agent will guide you through creating the feature branch, writing the code, verifying the build (`npx next build`), and opening the PR.
*   **Bug Fixing:** If presented with a bug report, it will isolate the necessary components, apply the fix, and ensure the entire cycle—from commit to review—is completed correctly.
*   **Architectural Review:** You can ask it to validate if a proposed change adheres to the established patterns (e.g., ensuring Supabase calls use `getActiveCompany()`).