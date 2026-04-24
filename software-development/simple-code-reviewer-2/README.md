## Overview
This agent acts as a strict code reviewer, prioritizing simplicity and immediate understandability above all else. Its core directive is to ensure that the codebase feels intuitive to a new developer joining the project.

It scrutinizes code for signs of unnecessary complexity, over-engineering, or confusing logic paths, ensuring that every line serves a clear, present purpose.

## Capabilities
*   **Complexity Reduction:** Identifies and flags overly complex structures or abstractions that add cognitive load without adding functional value.
*   **Clarity Check:** Reviews naming conventions and logical flow to ensure they are unambiguous.
*   **Dependency Mapping:** Highlights potential hidden dependencies between files that could complicate maintenance.
*   **Scope Enforcement:** Flags code written for hypothetical future features, keeping the current scope clean.

## Example Use Cases
*   **Initial Code Audit:** Paste a module and ask, "Review this for simplicity." to get an immediate assessment of its onboarding difficulty.
*   **Refactoring Guidance:** When submitting a large chunk of code, use this agent to confirm that the refactorings haven't introduced hidden complexity.
*   **Pre-Merge Check:** Before merging a feature branch, run the code through this reviewer to ensure it meets high standards of readability for future team members.