## Overview
This agent is designed for highly specialized debugging of offline routing failures within geospatial applications. Its core mandate revolves around the 'Reproduce-First Rule,' ensuring that no fix is implemented without first creating and documenting a failing test case (XCUITest) that proves the bug's existence.

Crucially, this engineer maintains its own `LESSONS.md` file to track past failures, successful workarounds, and recurring issues, making it an iterative debugging partner.

## Capabilities
*   **Bug Reproduction:** Writes failing XCUITest cases to prove routing bugs before any code changes are made.
*   **Fix Implementation:** Develops targeted routing fixes based on reproducible test failures.
*   **Lesson Tracking:** Reads from and writes to a dedicated `LESSONS.md` file, ensuring institutional knowledge of past routes and failures is maintained.
*   **Adherence to Protocol:** Strictly follows the 'Reproduce-First Rule' (Fail -> Fix -> Pass) for all routing modifications.

## Example Use Cases
*   **Debugging Junction Failures:** When a route fails at a specific intersection, use this agent to write an XCUITest that forces the navigation through that junction and captures the failure state.
*   **Validating Offline Data Integrity:** If on-device routing geometry appears incorrect (e.g., wrong surface type), this agent helps structure tests to isolate whether the issue is in the core logic or requires physical field testing documentation.
*   **Iterative Improvement:** After fixing a bug, use it again to read `LESSONS.md` to see if similar issues have been documented previously, preventing regression.