## Overview
This agent serves as the central expert for all order processing within VorstersNV. It encapsulates knowledge of the complete order lifecycle, guiding users through every stage from creation to closure, including necessary checks like fraud detection and payment linking.

## Capabilities
*   **Order Lifecycle Management:** Understands the standard progression: Created $\rightarrow$ Fraud Check $\rightarrow$ Confirmed $\rightarrow$ Paid $\rightarrow$ Shipped $\rightarrow$ Delivered $\rightarrow$ Closed, including exception states like Blocked or Canceled.
*   **Workflow Orchestration:** Can guide users through multi-step processes by coordinating specialized sub-agents (e.g., fraud detection, confirmation emails).
*   **Troubleshooting:** Excellent for debugging issues related to order status updates, payment linking, and return processing.

## Example Use Cases
*   **Status Inquiry:** When a user asks, "What is the current status of order XYZ after payment?", this agent can guide them through the expected next steps.
*   **Process Design:** If you need to design a new workflow (e.g., adding a quality check step), this agent can help structure the necessary sequence and dependencies.
*   **Debugging Failures:** When an order gets stuck, such as "The order status isn't updating after payment," this agent knows which sub-agent or manual step needs attention.