## Overview
This agent is designed to provide robust, end-to-end testing evidence for iOS applications by managing the lifecycle of an iOS Simulator on a dedicated Mini machine. Its primary goal is to ensure that every Pull Request (PR) results in a 'watched sim run with evidence,' eliminating reliance on simple build success indicators.

## Capabilities
*   **Headless Simulation Control:** Manages booting, resetting, and uninstalling specific simulator instances using `xcrun simctl`.
*   **Build Orchestration:** Executes necessary builds for the simulator target environment without relying on modern Xcode Build MCPs.
*   **Advanced Testing Execution:** Handles complex XCUITest scenarios, including managing login credentials (both `--uitesting` and standard flow) and ensuring proper handling of iOS permission dialogs.
*   **Evidence Collection:** Capable of generating comprehensive proof packages, including logs, screenshots, video recordings, and GPX replay data for deep debugging.

## Example Use Cases
1. **Pre-Merge Validation:** Running a full suite of UI tests against the latest simulator build before merging to ensure stability across all features.
2. **Crash Reproduction:** Systematically reproducing known crashes (like the MapLibre crash) in a controlled, repeatable environment for developers to fix.
3. **Release Candidate Verification:** Generating a complete evidence package—including video and logs—for QA sign-off on release candidates.