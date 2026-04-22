# Payment Flow

> ## Overview

This document describes the payment flow for YouAndINotAI, which uses Square as the sole payment processor. The flow includes both subscr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Payment Flow Documentation

## Overview

This document describes the payment flow for YouAndINotAI, which uses Square as the sole payment processor. The flow includes both subscription payments and Bot-Shield verification payments.

## Components

### 1. Payment Link Generation

- Users initiate payments through the billing router (`/billing/checkout-link`)
- The system creates a Square payment link using the Square API
- A checkout reference is generated and embedded in the payment note

### 2. Square Payment Processing

- Square processes the payment and sends a webhook notification
- The webhook is received by the Square webhook handler (`/webhooks/square-payment`)

### 3. Webhook Handling

#### Payment Completion

When a payment is completed, the webhook handler performs the following:

1. Verifies the Square webhook signature
2. Extracts payment information from the webhook payload
3. Resolves the user associated with the payment:
   - First tries to match via checkout reference
   - Falls back to Square customer ID
   - Finally tries to match by email address
4. Links Square customer ID to the user if not already linked
5. Processes the payment based on the tier:
   - For subscriptions (founding_member, 3_month, 12_month, royalty):
     - Updates user's subscription status
     - Sets subscription expiration date
     - Marks the verification event as completed if it matches the checkout reference
   - For Bot-Shield ($1 payment):
     - Validates the checkout binding
     - Creates a new verification event if one doesn't exist
     - Promotes user verification if ready
     - Sends welcome email if this is the user's first verification

#### Subscription Events

The webhook handler also processes subscription events:

1. Subscription creation: Activates the user's subscription
2. Subscription updates: Updates the subscription status (active/canceled)

### 4. Revenue Allocation

For each completed payment, the system reserves a revenue allocation record to t

*[truncated — see source for full prompt]*