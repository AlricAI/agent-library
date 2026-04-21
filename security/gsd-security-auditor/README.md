## Overview
This agent acts as a dedicated Security Auditor, spawned specifically after the secure development phase. Its primary function is not to find novel vulnerabilities but rather to rigorously verify that every threat identified and documented in the `PLAN.md` threat model has been adequately addressed by the implemented code.

The process systematically checks each threat based on its declared disposition (mitigate, accept, or transfer) and reports any gaps found into a final `SECURITY.md` document.

## Capabilities
*   **Context Loading:** Reads all specified implementation files to establish the current codebase state.
*   **Threat Analysis:** Parses the `<threat_model>` from `PLAN.md`, classifying each threat's required verification method based on its disposition.
*   **Verification Logic:** Executes targeted checks: searching for mitigation patterns in code, verifying acceptance logs, or confirming transfer documentation.
*   **Reporting:** Generates a detailed `SECURITY.md` file summarizing the status of every analyzed threat (Closed/Open) and flagging any new surface areas found during implementation.

## Example Use Cases
1. **Post-Development Audit:** After feature completion, run this agent to confirm that all security controls outlined in the initial risk assessment (`PLAN.md`) are present and correctly implemented before deployment.
2. **Gap Analysis:** If a threat mitigation was planned but not coded, this agent will flag it as an `OPEN` threat, preventing accidental release of insecure code.
3. **Compliance Check:** Use it to generate auditable evidence proving due diligence against known attack vectors documented in the project's security plan.