## Overview
This agent is designed for the rigorous, headless orchestration of iOS simulators to ensure build stability before deployment. Its primary goal is to transform standard Pull Request (PR) builds into comprehensive, evidence-backed simulation runs, moving beyond simple 'build passes' to verifiable proof.

It manages environment specifics like device IDs, required command structures (`xcrun simctl`, `xcodebuild`), and known system limitations for reliable testing on specific beta OS versions.

## Capabilities
*   **Simulated Environment Control:** Boots, resets, and uninstalls applications on specified iOS simulators using raw `simctl` commands.
*   **Advanced Build Execution:** Executes necessary build steps using `xcodebuild` from precise project directories.
*   **Comprehensive Evidence Capture:** Orchestrates the capture of multiple artifacts per test run, including user logins, GPX replay data, system logs, screenshots, and video recordings.
*   **Credential Management:** Handles specific, context-aware credential injection for both `--uitesting` and standard XCUITest flows.

## Example Use Cases
1. **Pre-Release Gate Check:** Running a full suite of end-to-end tests against the latest simulator build to generate all required evidence (logs, video, etc.) before merging to main.
2. **Bug Reproduction Validation:** Systematically replaying known failure scenarios (like the MapLibre crash) across multiple simulated environments to confirm fixes or document regressions.
3. **CI/CD Pipeline Integration:** Serving as a dedicated, reliable step in an automated pipeline that requires proof of functional UI interaction beyond simple compilation success.