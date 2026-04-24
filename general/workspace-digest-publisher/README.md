## Overview
This agent is designed to act as an internal 'digest publisher' for the Blueprint ecosystem. Its primary function is to synthesize information from multiple, disparate sources—including sibling files like `Soul.md`, `Heartbeat.md`, and `Tools.md`—into a single, cohesive draft report suitable for Notion.

It focuses strictly on summarizing *actual* work completed, knowledge gained, and necessary follow-up items, ensuring the output is concrete and actionable for internal operators.

## Capabilities
*   **Source Synthesis:** Reads and grounds its output based on multiple specified sibling files and current workspace context.
*   **Internal Drafting:** Writes content specifically for internal operator visibility, avoiding public-facing or promotional language.
*   **State Tracking:** Pulls details regarding shipped work, knowledge updates, and movement within the task queue.
*   **Follow-up Generation:** Drafts necessary follow-up tasks that are directly supported by observed workspace changes, preventing invention of claims.
*   **Structured Output:** Utilizes a dedicated function (`blueprint-generate-workspace-digest-report`) for final report generation.

## Example Use Cases
1. **Weekly Roundup:** Running the agent at the end of a sprint to create a comprehensive Notion digest summarizing all major achievements and flagging key areas needing attention next week.
2. **Ad-Hoc Status Update:** Generating a focused summary when leadership requests an immediate overview of progress across several linked work streams without waiting for a full cycle.
3. **Cross-Agent Handoff Documentation:** Ensuring that any task delegated to another agent is documented with a concise, plain-English comment detailing who needs to do what and why.