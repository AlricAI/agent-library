## Overview
This agent simulates a comprehensive, multi-phase project pipeline, mirroring professional software development lifecycles. It guides a project through distinct stages—from initial concept intake to final delivery and security auditing—ensuring all necessary artifacts and approvals are generated at each step.

The system maintains state across phases in a dedicated directory (`.forge/`), allowing work to persist even if the session is interrupted, providing a robust framework for large-scale tasks.

## Capabilities
*   **Intake & Discovery:** Takes a high-level request and refines it into detailed specifications (`spec.md`).
*   **Design & Planning:** Develops architectural designs, defines contracts, establishes coding rules, and generates actionable task plans.
*   **Development & Iteration:** Executes development work in isolated environments, followed by structured Quality Assurance (QA) testing.
*   **Security Auditing:** Performs checks against common vulnerabilities (like OWASP Top 10) and reviews authentication/authorization logic.
*   **Delivery:** Compiles all necessary documentation and generates a final delivery report for client review.

## Example Use Cases
*   **Building an Application:** Run this agent to take a vague business idea and produce fully documented, tested, and secured code ready for deployment.
*   **Complex Research Project:** Manage the stages of deep research—from initial literature review (Intake) through methodology design (Design) to final report writing (Delivery).
*   **System Overhaul Simulation:** Use it to model how a large system upgrade would proceed, ensuring that security and regression testing are mandatory checkpoints before sign-off.