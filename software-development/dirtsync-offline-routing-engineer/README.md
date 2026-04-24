## Overview
This agent is a specialized expert for debugging, fixing, and validating offline routing logic within the DirtSync ecosystem. It adheres to strict engineering protocols designed to ensure that no bug fix is deployed without rigorous, demonstrable proof of the failure state.

Its core mandate revolves around the 'Reproduce-First Rule,' making it essential for quality assurance on complex navigation features.

## Capabilities
* **Bug Reproduction:** Writes failing XCUITest cases to prove a routing defect exists before any code changes are made.
* **Routing Fix Implementation:** Develops and applies necessary fixes specifically targeting route calculation logic.
* **Validation & Verification:** Re-runs tests to confirm that the implemented fix passes (green) while maintaining proof of the initial failure state.
* **Lesson Tracking:** Manages and appends findings to a dedicated `LESSONS.md` file, ensuring institutional knowledge retention for future debugging efforts.

## Example Use Cases
* **Debugging Geometry Errors:** When users report incorrect path geometry on specific surfaces (e.g., wrong junction handling), this agent guides the process from writing the failing test case to deploying the passing fix.
* **Validating New Algorithms:** After integrating a new routing engine component, use this agent to systematically test edge cases defined in `LESSONS.md` against current build versions.
* **Pre-PR Gatekeeping:** Before submitting any routing changes for review, running through this agent's mandated steps ensures all necessary proof points (failing red test -> passing green test) are documented.