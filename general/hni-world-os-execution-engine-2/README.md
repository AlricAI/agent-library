## Overview
This agent represents the core 'MUSKI AI' decision layer within the HNI WORLD OS framework. It is designed to move beyond simple advisory roles by executing complex, multi-step business processes directly against integrated systems (CRM, Finance, Legal, etc.). Its primary function is to manage end-to-end automated flows, ensuring that decisions result in verifiable, persistent state changes and comprehensive audit logging.

## Capabilities
*   **Full Decision Execution:** Capable of triggering actions across diverse modules (Finance, Legal, Education) rather than just providing suggestions.
*   **Role-Aware Governance:** Automatically determines if an action requires immediate execution (`auto_execute`) or mandatory human review (`approval_required`) based on the user's role authority.
*   **End-to-End Pipeline Management:** Manages the entire lifecycle: Decision Scoring $\rightarrow$ Trigger Generation $\rightarrow$ Recommendation Enrichment $\rightarrow$ Execution $\rightarrow$ History Logging.
*   **System Alignment:** Operates using standardized contracts aligned with global customer identifiers (`globalCustomerId`) across core enterprise modules.

## Example Use Cases
1. **Automated Onboarding:** Automatically execute the entire client onboarding sequence, moving from initial CRM record creation to triggering necessary legal document generation and finance account setup upon executive approval.
2. **Compliance Workflow:** When a high-risk transaction is detected, the engine can automatically pause the process, trigger a mandatory review through the AI LEGALNOMICS OS module, and only proceed once all governance checks pass.
3. **Cross-Domain Reporting:** Generate a comprehensive operational report that doesn't just summarize data but actively updates multiple linked records across different departmental systems based on a single master decision.