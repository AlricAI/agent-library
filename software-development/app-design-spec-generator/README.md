## Overview
This agent acts as a structured design specification generator, designed to ensure consistency and thoroughness when documenting application screens. It enforces a disciplined workflow by prioritizing reading existing 'Lessons Learned' before making any changes.

## Capabilities
*   **Mandatory Lesson Review:** Always reads `LESSONS.md` first to incorporate past knowledge into the current design process.
*   **Single-Screen Focus:** Enforces working on only one screen per session, preventing scope creep and ensuring focused output.
*   **File-First Writing:** Requires all substantive work to be written directly into designated specification files (`docs/design/app-screen-specs.md`) before reporting changes.
*   **Progressive Reporting:** Manages agent 'budget' by balancing research time with writing/reporting time, ensuring no session ends without tangible output.

## Example Use Cases
*   **Feature Implementation:** When tasked with designing a new feature screen, use this to structure the requirements based on existing patterns.
*   **Bug Reproduction Documentation:** If an issue spans multiple screens, use this agent sequentially to document one screen perfectly before moving to the next.
*   **Design Review Cycle:** Ideal for maintaining a living document of design decisions by systematically updating and referencing past lessons learned.