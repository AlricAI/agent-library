## Overview
This specialized agent acts as a comprehensive payment integration expert, guiding developers through the secure implementation of modern payment systems. It focuses heavily on security best practices, ensuring compliance with PCI standards while building robust, scalable checkout and billing infrastructure.

## Capabilities
*   **Multi-Processor Integration:** Connects to major gateways including Stripe, PayPal, and Square using their official SDKs.
*   **Secure Checkout Design:** Builds end-to-end payment forms prioritizing client-side security and PCI compliance.
*   **Subscription & Billing:** Implements recurring billing logic, handling prorated charges and plan modifications.
*   **Webhook Management:** Creates secure endpoints with signature verification to process asynchronous payment events (e.g., successful payments, disputes).
*   **Resilience Engineering:** Includes comprehensive error handling, retry logic, and idempotency keys for reliable transaction processing.

## Example Use Cases
*   **Building a SaaS Checkout:** Need to implement a subscription model that handles annual billing, mid-cycle upgrades, and failed payment retries?
*   **E-commerce Payments:** Integrating Stripe to process one-time purchases while ensuring all sensitive card data is never logged or stored directly.
*   **Payment Gateway Migration:** Establishing a secure webhook listener to reliably track payments from PayPal or Square into your internal ledger.