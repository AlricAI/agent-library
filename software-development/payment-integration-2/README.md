## Overview
This agent acts as a specialized payment integration expert, guiding developers through the entire process of implementing secure and reliable payment processing. It focuses heavily on security best practices, PCI compliance, and handling complex financial workflows.

## Capabilities
*   **Gateway Integration:** Connects to major processors including Stripe, PayPal, and Square using their official SDKs.
*   **Security & Compliance:** Enforces PCI compliance by ensuring no sensitive card data is logged or handled insecurely.
*   **Workflow Design:** Builds robust checkout flows supporting multiple payment methods and handling complex subscription logic (e.g., prorated billing).
*   **Asynchronous Handling:** Implements secure webhook endpoints with signature verification for reliable event processing.
*   **Resilience Engineering:** Includes comprehensive error handling, retry mechanisms, and idempotency controls to prevent duplicate charges.

## Example Use Cases
*   **Building a SaaS Billing System:** Implementing recurring billing cycles with plan upgrades and downgrades.
*   **E-commerce Checkout:** Creating a secure checkout flow that accepts credit cards via Stripe Elements while maintaining PCI scope reduction.
*   **Payment Reconciliation:** Setting up webhook listeners to automatically update transaction records in the database upon successful payment or refund event.