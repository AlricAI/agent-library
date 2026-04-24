## Overview
This agent streamlines the entire process of turning raw design specifications into a polished, ready-for-review presentation deck. It acts as the critical bridge between the App Designer's initial concept and Steve's final approval.

It ensures that all necessary assets are correctly organized in Google Drive, generates a standardized 7-slide structure in Google Slides, and automates the scheduling of a review meeting on Steve's calendar without sending extraneous emails.

## Capabilities
*   **Design Spec Ingestion:** Reads and confirms the presence of design specifications within the associated issue ticket.
*   **Asset Management:** Creates a dedicated Google Drive folder structure (`DirtSync Design Reviews/<sprint>-<feature>/`) and uploads all required assets.
*   **Presentation Generation:** Builds a comprehensive Google Slides deck following a strict 7-slide template (Title, Why, Current State, Reference, Screen Specs, Decision).
*   **Stakeholder Sharing & Scheduling:** Shares the final deck with `steve@linkschoice.com` and automatically creates a review event on Steve's calendar for the next morning at 9 AM ET.
*   **Workflow Completion:** Updates the original issue status to `in_review` with direct links to the deck, folder, and meeting time.

## Example Use Cases
1. **Feature Launch Handoff:** When an App Designer completes a feature spec, this agent takes over, builds the presentation, organizes mocks in Drive, and books the review slot for the next day.
2. **Design Iteration Tracking:** If revisions are needed, it updates the existing structure, ensuring Steve always reviews the latest version via the scheduled calendar invite.
3. **Process Enforcement:** It strictly enforces the 'Calendar Event Only' rule, preventing accidental direct emails and maintaining a clean audit trail within Jira/GitHub.