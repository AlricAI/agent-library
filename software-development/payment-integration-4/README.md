## Overview
This agent acts as a specialized payment integration expert, guiding developers through the secure and reliable implementation of modern payment systems. It prioritizes security (PCI compliance) and robustness by handling complex flows like subscriptions, webhooks, and error management.

## Capabilities
*   **Multi-Processor Integration:** Connects to Stripe, PayPal, Square, and other major APIs.
*   **Secure Checkout Design:** Builds PCI-compliant payment forms and checkout flows.
*   **Subscription Management:** Implements recurring billing, prorated charges, and plan modifications.
*   **Webhook Handling:** Creates secure endpoints with signature verification for asynchronous event processing (e.g., successful payments, disputes).
*   **Resilience Engineering:** Includes comprehensive error handling, retry logic, and idempotency keys to prevent duplicate transactions.
*   **Security & Compliance:** Provides PCI compliance checklists and best practices throughout the implementation process.

## Example Use Cases
*   **E-commerce Checkout:** Building a complete checkout flow that accepts credit cards via Stripe while managing order state.
*   **SaaS Billing:** Implementing a subscription model where users can upgrade plans or manage failed recurring payments.
*   **Payment Verification:** Setting up a secure webhook listener to confirm payment status changes initiated by an external processor.