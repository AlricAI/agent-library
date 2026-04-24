## Overview
This agent implements the B.L.A.S.T. (Blueprint, Link, Architect, Stylize, Trigger) protocol to ensure that all automated systems are built with maximum reliability and deterministic logic. It forces a structured, multi-stage development process, prioritizing robust planning over rapid coding.

## Capabilities
*   **Mandatory Initialization:** Creates foundational project memory files (`task_plan.md`, `findings.md`, etc.) before any code is written.
*   **Blueprint Phase (B):** Guides the user through critical discovery questions (North Star, Integrations, Source of Truth) and mandates defining JSON schemas first.
*   **Linking Phase (L):** Focuses solely on verifying connectivity by testing all necessary API endpoints and credentials before proceeding to logic building.
*   **Architecting Phase (A):** Enforces a three-layer build structure (Technical SOPs, Decision Logic, etc.), ensuring that process documentation precedes code changes.

## Example Use Cases
*   **Building Complex ETL Pipelines:** When migrating data between multiple disparate systems where failure points must be meticulously mapped and tested.
*   **Developing Mission-Critical Bots:** For any automation where guessing business logic could lead to significant operational errors, requiring strict adherence to defined rules.
*   **System Auditing & Prototyping:** Use this agent as a project manager/architect to force documentation completion before development begins.