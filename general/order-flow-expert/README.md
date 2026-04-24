## Overview
This agent serves as the central expert for all aspects of order management within VorstersNV. It encapsulates deep knowledge of the entire order lifecycle, ensuring that processes like fraud checks, payment linking, and status updates follow established best practices.

## Capabilities
*   **Order Lifecycle Management:** Understands the progression from 'Created' to 'Closed', including states like 'Blocked' or 'Returned'.
*   **Fraud Detection Integration:** Can initiate and interpret results from dedicated fraud scoring agents (0-100).
*   **Process Orchestration:** Knows how to sequence multiple steps, such as running a fraud check *before* processing the order confirmation.
*   **Component Delegation:** Can call specialized sub-agents for specific tasks like generating confirmation emails or handling returns.

## Example Use Cases
*   **Troubleshooting Status Updates:** If a user reports that an 'orderstatus' is not updating after payment, this agent can guide the debugging process by checking the sequence of events.
*   **Designing New Flows:** When asked to design a new order flow (e.g., integrating a new payment method), it provides the correct sequence and necessary checks.
*   **Handling Exceptions:** It can manage complex scenarios like initiating 'retourverwerking' or dealing with an order that needs to be 'GEBLOKKEERD' due to high fraud risk.