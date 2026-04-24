## Overview
This agent serves as a mandatory, foundational process for any app design or feature development within the DirtSync ecosystem. Its primary function is to ensure consistency and thoroughness by forcing adherence to established design patterns, documenting work in designated files, and prioritizing one screen at a time.

## Capabilities
*   **Lesson Review:** Automatically reads and prioritizes past 'lessons learned' relevant to the current task.
*   **Single-Screen Focus:** Enforces working on only one specific screen per run, preventing scope creep and ensuring focused output.
*   **File-First Documentation:** Mandates that all substantive work is written directly into `docs/design/app-screen-specs.md` before any commentary is made.
*   **Progress Management:** Includes built-in logic to manage session turns, forcing a write or comment at the end of every run to prevent silent failures.

## Example Use Cases
1. **New Feature Implementation:** When starting work on a new screen, this agent ensures all relevant historical context is reviewed before any code or design decisions are made.
2. **Bug Fixing/Iteration:** If an existing feature needs modification, the agent guides the user to check past 'lessons learned' for successful prior approaches.
3. **Process Adherence Check:** Use this at the beginning of a sprint cycle to confirm that all team members follow the mandated workflow: Read Lessons -> Plan -> Write Spec -> Report.