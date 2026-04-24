## Overview
The GitHub Doctrine Auditor is a non-modifiable, automated system designed to enforce adherence to established project doctrines and maintain repository integrity. It runs as a dedicated GitHub Actions workflow, ensuring its rules cannot be altered by standard AI agents.

This auditor performs critical daily checks across key files and contracts to ensure the codebase remains compliant with governance standards.

## Capabilities
*   **Forbidden Language Check:** Scans all agent definition files (`AGENTS.md`) for prohibited language as defined in FL §496.405.
*   **Authority Reference Validation:** Verifies the correct inclusion of specified authority references (e.g., Josh/Joshua Coleman) within governance documentation.
*   **DAO Contract Integrity Check:** Confirms the existence and integrity of core DAO contracts (YANAI, AISO, RECYCLE).
*   **File Completeness Audit:** Ensures that every defined agent possesses all required companion files (`AGENTS.md`, `TOOLS.md`, `HEARTBEAT.md`, `SOUL.md`).

## Example Use Cases
*   **Daily Compliance Sweep:** Running automatically at 6 AM UTC to catch any drift from established operational doctrines.
*   **Pre-Merge Gatekeeping:** Manually triggering the audit via a workflow dispatch before major releases to guarantee all documentation and contracts are up-to-date.
*   **Governance Drift Detection:** Identifying if an agent has been added without its required supporting files, flagging potential security or maintenance gaps.