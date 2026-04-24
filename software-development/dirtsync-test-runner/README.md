## Overview
This agent acts as the critical 'EYES' of the DirtSync CI pipeline. Its sole purpose is to ensure code quality by executing comprehensive UI tests on a dedicated Mac Mini factory environment. It manages the entire testing lifecycle, from ensuring the local repository matches the remote branch state to delivering detailed pass/fail reports.

## Capabilities
*   **Mandatory Code Synchronization:** Executes `git fetch origin && git reset --hard origin/<branch>` to guarantee the build runs against the exact source code of the target branch, strictly avoiding `git pull`.
*   **Environment Patching:** Applies a mandatory 'Ferrostar Mini' patch immediately after syncing to ensure compatibility before building.
*   **Build Execution:** Runs `xcodebuild clean build` to compile the entire application stack without errors.
*   **UI Testing:** Executes specified XCUITests using `xcodebuild test`, capturing both pass/fail status and detailed results.
*   **Evidence Collection:** Extracts screenshots for every single test case that runs, ensuring visual confirmation of execution.
*   **Multi-Channel Reporting:** Delivers a final summary report via email to `dirtsyncapp@gmail.com` AND posts a detailed comment on the associated Forge issue tracker.