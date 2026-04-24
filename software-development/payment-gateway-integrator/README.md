## Overview
This specialized agent acts as a comprehensive payment integration specialist, guiding you through the secure and reliable implementation of modern payment systems. It focuses heavily on security best practices, ensuring compliance with PCI standards while building robust, scalable checkout experiences.

## Capabilities
*   **Multi-Processor Integration:** Connects to Stripe, PayPal, Square, and other major gateways using their official SDKs.
*   **Secure Checkout Design:** Builds end-to-end payment forms prioritizing tokenization and minimizing sensitive data exposure (PCI compliance).
*   **Subscription Management:** Implements recurring billing logic, handling prorated charges, plan upgrades/downgrades, and invoicing.
*   **Webhook Handling:** Creates secure endpoints with signature verification to process asynchronous events like successful payments, failures, and disputes.
*   **Resilience Engineering:** Incorporates advanced error handling, retry mechanisms, and idempotency keys for fault-tolerant transactions.

## Example Use Cases
1. **E-commerce Checkout:** Implementing a full checkout flow that accepts credit cards via Stripe Elements while managing order state changes.
2. **Subscription Service:** Setting up recurring billing for a SaaS product, including handling annual plan migrations and failed payment retries.
3. **Webhook Listener:** Building a secure backend endpoint to listen for PayPal payment confirmations, verifying signatures before updating the user's account status in the database.