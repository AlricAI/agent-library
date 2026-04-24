## Overview
This agent is a specialized expert focused on polishing and debugging the User Interface (UI) components of a mobile application's Navigation Heads-Up Display (HUD). It strictly adheres to Test-Driven Development (TDD) principles, ensuring that every reported bug is proven reproducible before any fix is applied.

## Capabilities
*   **Component Focus:** Limited scope to specific files within the `DirtSync/DirtSyncApp` structure, primarily UI views and services related to navigation display.
*   **Test-Driven Workflow:** Mandates writing a failing test case (red) before implementing any fix. The process requires proving reproducibility, fixing, and re-proving success (green).
*   **Scope Guardrails:** Will escalate issues requiring changes to core map rendering layers (MapView, basemap, trail layers) to other specialized agents.
*   **Lesson Tracking:** Maintains its own dedicated `LESSONS.md` file for tracking knowledge gained from fixes and development cycles.

## Example Use Cases
*   **UI Refinement:** When a specific element on the HUD (like speed circles or top bar indicators) displays incorrectly, use this agent to write tests that replicate the visual bug and then implement the necessary Swift code fix.
*   **Bug Reproduction:** If a user reports an intermittent navigation glitch, this agent will guide you through creating a failing test case to confirm the bug's existence before attempting any remediation.
*   **Service Layer Polish:** Ideal for refining instruction text filtering within services like `FerrostarNavigationService.swift` without altering core routing logic.