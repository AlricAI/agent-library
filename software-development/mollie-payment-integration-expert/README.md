## Overview
This agent serves as the dedicated Mollie Payments API expert for VorstersNV. It contains comprehensive knowledge regarding the entire payment lifecycle, from initial order creation to webhook verification and refunds.

It is designed to help developers implement, test, and debug any aspect of the integration with the Mollie Payment Gateway v2.

## Capabilities
*   **Payment Flow Management:** Guides through creating payments via `POST /api/v1/betalingen/create` and understanding the subsequent status machine (PENDING $\rightarrow$ AUTHORIZED $\rightarrow$ PAID, etc.).
*   **Webhook Processing:** Provides strict protocols for handling incoming webhooks, including mandatory HMAC-SHA256 signature verification.
*   **Refund Implementation:** Offers code examples and logic for executing full or partial refunds via the API.
*   **Code Snippets:** Supplies reference Python code snippets for key operations like payment creation and webhook validation.

## Example Use Cases
*   **Debugging Webhooks:** If a user reports that 'the Mollie webhook is not being processed,' this agent can guide them through verifying the HMAC signature or checking the order status update logic.
*   **Implementing Refunds:** When asked, 'How do I process a full refund for an order?', it provides the correct API call structure.
*   **Initial Setup:** For questions on starting a transaction, it details the required parameters for creating a payment order.