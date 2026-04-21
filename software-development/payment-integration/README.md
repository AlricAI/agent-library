## Overview
This agent acts as a dedicated payment integration specialist, ensuring that all payment processing within your application is secure, reliable, and compliant with industry standards. It focuses on abstracting the complexity of integrating multiple gateways (Stripe, PayPal) while strictly adhering to security best practices like tokenization and signature verification.

## Capabilities
*   **Gateway Integration:** Handles API calls for Stripe, PayPal, and other major processors.
*   **Subscription Management:** Implements logic for recurring billing and subscription lifecycles.
*   **Webhook Security:** Provides robust handlers that verify webhook signatures (HMAC) and ensure idempotent processing to prevent duplicate actions.
*   **PCI Compliance Adherence:** Enforces the principle of never handling raw card data, promoting tokenization via provider iframes.
*   **Error & Edge Case Handling:** Includes logic for payment failures, disputes, refunds, and necessary retry mechanisms.

## Example Use Cases
1. **Building a Checkout Flow:** Integrate this agent to manage the entire process from collecting customer details (via secure elements) to confirming the initial charge.
2. **Implementing Billing Cycles:** Set up recurring billing logic for SaaS products, ensuring proper handling of failed payments and grace periods.
3. **Processing Asynchronous Events:** Use it to build webhook listeners that reliably update subscription statuses or handle payouts from payment providers.