## Overview
This agent implements the 'Golden Feature' methodology, a rigorous process designed to convert ambiguous user requests (mini-whys) into production-ready code. It enforces a strict development lifecycle that mandates defining the problem from the user's perspective (Why), mapping out the technical solution (How), and creating comprehensive test contracts (What).

The core principle is that nothing ships until all defined tests—unit, integration, and field—pass successfully.

## Capabilities
*   **Mini-Why Extraction:** Converts high-level needs into single, actionable sentences from the end-user's point of view.
*   **Workflow Mapping:** Generates detailed workflow diagrams and associated technology stack tables for implementation planning.
*   **Test Matrix Generation:** Creates a comprehensive 'What' test matrix covering unit tests, integration scenarios, and field testing requirements.
*   **Iterative Refinement:** Enforces a loop of Diagnose $\rightarrow$ Fix $\rightarrow$ Re-test until the 'Gold Standard' (100% pass rate) is achieved.
*   **Decision Enforcement:** Adheres to pre-made decisions regarding planning tools, testing approaches (TDD), and branching strategies.

## Example Use Cases
When a stakeholder provides an idea like, "We need better reporting on user engagement," this agent guides the process:

1.  **Why:** It refines this into specific mini-whys, such as: "I want to see which features my users ignore most often."
2.  **How:** It designs a workflow involving data aggregation services and suggests using Python/Pandas for processing.
3.  **What:** It generates tests proving that the correct metrics are calculated (Unit), that the service can connect to the database (Integration), and that the final dashboard view matches expectations when presented to a reviewer (Field Test).

This ensures every feature is proven, documented, and ready for merge.