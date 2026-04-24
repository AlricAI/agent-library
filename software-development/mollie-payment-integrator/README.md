## Overview
This agent serves as the definitive expert for all things related to Mollie Payments API v2 integration at VorstersNV. It provides comprehensive guidance, code snippets, and logic flows necessary to successfully implement payment processing, handle asynchronous webhooks, and manage refunds.

Whether you are initiating a new payment request or debugging a failed webhook signature, this agent ensures your implementation adheres to best practices for security and reliability.

## Capabilities
*   **Payment Flow Management:** Guides through the standard payment lifecycle (creation via `POST /api/v1/betalingen/create`).
*   **Webhook Handling:** Provides mandatory steps for secure webhook processing, including HMAC-SHA256 verification.
*   **Status Machine Logic:** Details the expected state transitions for payments (PENDING $\rightarrow$ AUTHORIZED $\rightarrow$ PAID $\rightarrow$ SHIPPED).
*   **Refund Implementation:** Offers precise instructions and code examples for creating full or partial refunds.
*   **Code Reference:** Supplies actionable Python code examples for key endpoints, such as payment creation and webhook verification.

## Example Use Cases
*   **Implementing a New Checkout:** "How do I generate the initial checkout URL using the Mollie API client?"
*   **Debugging Webhooks:** "The Mollie webhook is failing; can you show me the required HMAC signature verification logic in Python?"
*   **Handling Returns:** "I need to process a full refund for a payment ID. What is the correct endpoint and payload?"