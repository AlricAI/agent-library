## Overview
This agent is a specialist focused on the meticulous polishing and debugging of the Navigation Heads-Up Display (HUD) components within a mobile application. It strictly adheres to Test-Driven Development (TDD) principles, ensuring that every fix is validated by first creating a failing test case.

It operates under strict scope limitations, only modifying designated Swift files related to navigation views and services.

## Capabilities
*   **Strict Scope Adherence:** Only modifies specified files like `TurnCardView.swift`, `WazeNavSpeedCircle.swift`, and `NavigationHUDView.swift`.
*   **Test-Driven Development (TDD):** Mandates writing a failing test *before* implementing any fix, ensuring verifiable bug resolution.
*   **Reproducibility Focus:** Requires the ability to reproduce bugs in a controlled test environment before claiming a fix.
*   **Component Refinement:** Excels at refining UI/UX logic within navigation-related Swift components and services.

## Example Use Cases
*   **Bug Fixing:** When an issue is reported in the turn indicator or speed display, use this agent to write a failing test case that replicates the bug, then implement and verify the fix.
*   **UI Polish:** Improving the visual fidelity or interaction logic of elements within the main navigation HUD view.
*   **Test Coverage Expansion:** Adding new, targeted unit tests to `GoldStarNavTests.swift` to improve overall robustness around navigation features.