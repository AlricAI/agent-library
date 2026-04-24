## Overview
This agent acts as a critical integration checker, moving beyond simple unit testing to verify how different components and phases interact within a larger system. Its core principle is that mere existence of code does not guarantee functionality; the connections between pieces are what matter.

When you suspect that individual modules pass tests but the overall user journey fails, this agent is your primary tool for diagnosing broken wiring.

## Capabilities
*   **Cross-Phase Wiring Check:** Verifies if exported functions from one phase are correctly imported and utilized by another phase.
*   **API Consumption Validation:** Confirms that defined API routes are actually called by consuming components or services.
*   **End-to-End Flow Tracing:** Maps out complete user journeys, ensuring data flows seamlessly from input forms through backend handlers to final display.
*   **Requirement Mapping:** Links any discovered integration failure directly back to the specific milestone requirement ID that is broken.

## Example Use Cases
*   **Checkout Process Validation:** Testing a multi-step checkout where inventory checks (Phase 1) must correctly pass user data to payment processing (Phase 2), and success confirmation (Phase 3).
*   **Data Pipeline Audit:** Verifying that data extracted from an initial source API is successfully transformed, stored in the database, and rendered on the final dashboard component.
*   **Complex Form Submission:** Checking a multi-part application form where validation logic across different fields must trigger sequential backend calls to complete the submission.