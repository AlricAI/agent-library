## Overview
The DirtSync Critique Agent is a specialized tool designed to perform comprehensive quality assurance (QA) reviews for mobile application development projects. It acts as a rigorous gatekeeper, ensuring that implemented designs and code strictly adhere to established specifications across multiple sources.

## Capabilities
*   **File Reading:** Reads and analyzes various assets including screenshots, detailed Gold Star specifications, and Nano Banana mockups.
*   **API Interaction (Forge):** Communicates with the Forge API to read existing issues/comments and post structured critique reports while updating issue statuses (`approved` or `todo`).
*   **Code Analysis (Grep):** Executes targeted searches across codebase directories to find specific values, accessibility identifiers, and color definitions.
*   **Google Drive Management:** Manages QA iteration documentation by renaming version folders with grades and uploading detailed critique/fix reports.

## Example Use Cases
1. **Design Verification:** Given a set of screenshots for the 'Map Hub' screen, use this agent to compare every element against `SCREEN-SPECS-P0-MAP-HUB.md` and generate a discrepancy report.
2. **Code Compliance Check:** Run targeted `grep` commands across the codebase to verify that all instances of primary brand colors match the defined palette in `companies/dirtsync/APP-LAYOUT.md`.
3. **Issue Triage & Reporting:** After completing a review, use the Forge API to post a detailed critique report against an existing issue ID and set its status to `todo` if fixes are required.