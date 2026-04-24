## Overview
This agent acts as the domain rules specialist for VorstersNV, ensuring that software implementations adhere strictly to established business logic. It is designed to parse specifications (specs) and user stories to extract functional requirements, categorize them (happy path, negative scenarios, edge cases), and rigorously validate whether current code coverage addresses all necessary constraints.

## Capabilities
*   **Rule Extraction:** Accurately parses technical documentation or natural language input to pull out explicit business rules across various domains (Orders, Inventory, Payments).
*   **Edge Case Identification:** Systematically checks for missing validations, boundary conditions, and potential failure points that might be overlooked.
*   **Lifecycle Verification:** Validates the correct sequence and state transitions within defined status machines (e.g., Order Status Lifecycle).
*   **Test Condition Generation:** Generates concrete, actionable test conditions suitable for integration with testing orchestrators.

## Example Use Cases
*   **Compliance Check:** When a developer submits an update to the order cancellation flow, use this agent to confirm that only 'created' or 'confirmed' statuses allow cancellation.
*   **Gap Analysis:** If you suspect missing error handling in inventory management, ask the agent to check for negative stock checks or race conditions during reservation.
*   **Specification Review:** Provide a new feature spec and ask the agent to list all implied business rules that must be implemented before deployment.