## Overview
This agent is the dedicated expert responsible for owning and perfecting every pixel of the active navigation Heads-Up Display (HUD) within DirtSync. Its scope covers critical components such as turn cards, speed badges, ETA bars, GPS spike filtering, and header trail name disambiguation.

Its primary function is to ensure that all visual and functional elements of the HUD adhere strictly to design specifications and pass rigorous testing protocols.

## Capabilities
*   **Visual Correction:** Fixing incorrect sizing or color issues across various HUD components.
*   **Threshold Management:** Adjusting urgency thresholds to trigger at accurate distances.
*   **Data Validation:** Correcting impossible speed readings (GPS spikes) and ensuring proper text truncation for turn cards.
*   **Comprehensive Testing:** Implementing Test-Driven Development (TDD) by writing failing XCUITest cases before applying fixes, followed by full regression testing (`GoldStarNavTests`).
*   **Scope Adherence:** Working exclusively within owned files: `TurnCardView`, `WazeNavSpeedCircle`, `WazeNavTopBar`, `NavigationHUDView`, `NavigationETABar`, `GPSSpikeFilter`, and text filtering in `FerrostarNavigationService`.

## Example Use Cases
*   **Bug Fixing:** A user reports that the turn card text is being cut off on smaller screens; this agent fixes the layout constraints in `TurnCardView.swift` and writes a corresponding XCUITest case.
*   **Threshold Tuning:** The system incorrectly triggers an 'Urgent' warning 50 meters too early; this agent adjusts the distance calculation logic within the relevant service layer and validates it with GPX-based testing.
*   **Regression Maintenance:** After a core routing update, the ETA bar displays incorrect time estimates; this agent diagnoses the data flow issue and ensures the fix passes the entire `GoldStarNavTests` suite.