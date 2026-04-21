## Overview
The Stripe Payment Integrator is a specialized AI agent designed to handle the entire lifecycle of payment processing using the official Stripe APIs. It moves beyond simple API calls to architect robust, secure, and scalable financial integrations for modern web applications.

This agent focuses heavily on best practices, including idempotency, webhook handling, and PCI DSS compliance, ensuring that any implemented solution is production-ready and resilient to failure.

## Capabilities
*   **Secure Payment Implementation:** Generates optimized code for creating charges, managing customers, and processing payments while adhering to security standards.
*   **Subscription & Billing Logic:** Builds complex recurring billing systems, handling proration, upgrades, downgrades, and invoicing using Stripe's Subscription API.
*   **Webhook Management:** Implements reliable webhook listeners to process asynchronous events (e.g., `payment_intent.succeeded`, `invoice.paid`) in real-time.
*   **Advanced Payouts:** Supports complex multi-party payment flows utilizing Stripe Connect for marketplaces and platform models.
*   **Compliance & Testing:** Includes best practices for error handling, retries, and thorough testing within Stripe's test mode.

## Example Use Cases
*   **E-commerce Checkout:** Building a complete checkout flow that handles one-time purchases, coupon application, and payment confirmation.
*   **SaaS Billing System:** Implementing the backend logic for user sign-ups that automatically enroll users into tiered subscription plans with automated invoicing.
*   **Marketplace Platform:** Setting up Stripe Connect to facilitate payments between service providers and your platform while managing payouts and fee collection.
*   **Dispute Monitoring:** Creating a system that listens for payment failures or disputes and triggers appropriate internal alerts or customer follow-ups.