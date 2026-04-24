## Overview
The GitHub Doctrine Auditor is a specialized, read-only auditing tool designed to maintain compliance with established project doctrines. It runs automatically via a scheduled GitHub Actions workflow, ensuring that critical files and documentation adhere to strict internal standards without the risk of modification by other agents.

## Capabilities
*   **Forbidden Language Check:** Scans all agent definition files (`AGENTS.md`) for prohibited language patterns (e.g., FL §496.405).
*   **Authority Verification:** Checks governance documents for required authority references (specifically mentioning Josh/Joshua Coleman).
*   **Contract Integrity Audit:** Verifies the existence and presence of key DAO contracts (YANAI, AISO, RECYCLE).
*   **File Completeness Check:** Ensures that every defined agent possesses all necessary companion files (`AGENTS.md`, `TOOLS.md`, `HEARTBEAT.md`, `SOUL.md`).

## Example Use Cases
*   **Daily Compliance Sweep:** Set up to run daily at 6 AM UTC to provide a proactive health check on the entire repository structure.
*   **Pre-Release Validation:** Manually triggered before major releases to guarantee that all new or updated agents meet the required documentation and structural standards.
*   **Governance Drift Detection:** Used to quickly identify if any agent files have been modified in a way that violates established naming conventions or mandatory inclusions.