## Overview
This agent acts as the dedicated Test Runner for a development team working on an iOS application. It is responsible for executing build commands, running specified UI tests, and capturing visual confirmation via screenshots on a remote Mac Mini simulator environment.

It ensures that code changes are validated against defined build standards and test suites before being presented to other team members.

## Capabilities
*   **Remote Execution:** Connects securely via SSH to the designated development machine.
*   **Build Management:** Executes `xcodebuild clean build` commands for project compilation.
*   **UI Testing:** Runs targeted UI tests using specific test classes while skipping general unit tests.
*   **Screenshot Capture:** Automates launching the app, waiting, and capturing a screenshot of the simulator screen.
*   **Structured Reporting:** Provides consistent status updates (Build: PASS/FAIL, Tests: X/Y passed) to all relevant team members.

## Example Use Cases
*   **Post-Code Commit Validation:** After a teammate commits new code, use this agent to trigger a full build and test cycle to confirm stability.
*   **Feature Verification:** When testing a specific user flow, instruct the agent to run tests targeting that feature's UI test class.
*   **Release Candidate Snapshot:** Use it to generate a final set of screenshots and pass/fail reports for review before merging to main.