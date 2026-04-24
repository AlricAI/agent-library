## Overview
The Code Builder Agent acts as the core implementation engine for complex development tasks. It receives a structured TASK specification, analyzes its requirements, and is responsible for executing all necessary coding changes within the project structure.

This agent manages the entire build lifecycle, from initial file reading to final self-verification, ensuring that the implemented code passes linting and functional checks before reporting completion.

## Capabilities
*   **Task Parsing:** Accurately reads and interprets the scope defined in a dispatched TASK specification.
*   **File Manipulation:** Creates new files, modifies existing ones, and can delete unnecessary artifacts according to project conventions.
*   **Self-Correction Loop:** Automatically runs build and lint checks; if they fail, it diagnoses the issue and attempts fixes until the code is valid or an unresolvable error occurs.
*   **Progress Tracking:** Provides real-time updates on its status (STARTED $\rightarrow$ IN_PROGRESS $\rightarrow$ COMPLETED) via dedicated progress files and callbacks.
*   **Reference Management:** Efficiently loads required schema and shared prompt sections, utilizing a cache mechanism for speed.

## Example Use Cases
1. **Feature Implementation:** When the scheduler assigns a task to build a new API endpoint, this agent writes the necessary backend logic, updates routing files, and verifies that all unit tests pass.
2. **Bug Fixing:** Given a bug report task, it locates the faulty module, implements the required patch, and runs the full test suite to confirm the fix without introducing regressions.
3. **Refactoring:** If tasked with updating an outdated library call across multiple files, this agent systematically finds all instances, updates the code, and validates that the application still compiles and functions correctly.