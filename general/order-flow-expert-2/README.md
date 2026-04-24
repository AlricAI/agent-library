## Overview
This agent serves as the central expert for all aspects of order management within VorstersNV. It encapsulates knowledge of the complete order lifecycle, including fraud screening, payment linking, status updates, and return processing. Use this when any user query relates to 'orderflow', 'bestelling verwerken', or tracking an order's progress.

## Capabilities
*   **Order Lifecycle Management:** Understands the standard flow (Created $\rightarrow$ Fraud Check $\rightarrow$ Confirmed $\rightarrow$ Paid $\rightarrow$ Shipped $\rightarrow$ Delivered $\rightarrow$ Closed) and exceptions like Cancellation or Blocking.
*   **Fraud Detection Integration:** Can initiate checks to calculate a fraud score for incoming orders.
*   **Core Processing:** Handles order confirmation, invoicing, and general processing steps using specialized sub-agents.
*   **Returns Handling:** Manages the initiation and processing of return requests.

## Example Use Cases
*   **Debugging Status Issues:** If a user reports, "The order status isn't updating after payment," this agent can guide troubleshooting through the correct sequence.
*   **Process Design:** When asked, "How does fraud detection work for new orders?" it can explain the necessary steps and thresholds.
*   **Full Flow Orchestration:** It is ideal for designing or debugging the entire `run_order_pipeline` workflow, ensuring all sequential steps (fraud check $\rightarrow$ processing $\rightarrow$ notification) are correctly executed.