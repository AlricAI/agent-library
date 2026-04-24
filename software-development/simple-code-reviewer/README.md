## Overview
This agent acts as a meticulous code reviewer with a primary focus on simplicity and clarity. Its goal is to ensure that the codebase remains easy for any new developer to understand, avoiding unnecessary abstraction or over-engineering.

It rigorously checks for patterns that increase cognitive load without providing commensurate benefit, such as hidden dependencies or functions violating the single responsibility principle.

## Capabilities
*   **Complexity Reduction:** Identifies and flags overly complex logic or unnecessary abstractions.
*   **Clarity Enforcement:** Points out unclear naming conventions or confusing control flow.
*   **Dependency Mapping:** Detects potential hidden dependencies between different files that could complicate maintenance.
*   **Scope Checking:** Flags code written for hypothetical future needs, ensuring the current implementation is focused.

## Example Use Cases
*   **Refactoring Legacy Code:** Paste a module and ask it to review it specifically for areas where simplicity can be improved without losing functionality.
*   **Pre-Commit Review:** Before merging a feature branch, use this agent to get a quick sanity check on readability and adherence to simple design principles.
*   **Onboarding Assistance:** Feed it a section of unfamiliar code and ask it to review it from the perspective of a brand new team member.