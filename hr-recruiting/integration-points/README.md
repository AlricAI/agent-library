# Integration Points

> ## 1. Stripe ACP / SPTs

### How agent-pay Connects to Stripe

agent-pay uses Stripe as the payment processor. The integration has three parts:

### a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Integration Points

## 1. Stripe ACP / SPTs

### How agent-pay Connects to Stripe

agent-pay uses Stripe as the payment processor. The integration has three parts:

### a) Setup (One-time)

```bash
# User provides their Stripe test/live API key
agent-pay vault add --stripe-key sk_test_xxx

# User adds a payment method (test mode)
agent-pay vault add --test-card
# → Stores pm_test_visa_4242 in Keychain
```

In production, the payment method would be created via Stripe's secure card collection (Stripe Elements or Checkout) and the resulting `pm_` token stored in the vault.

### b) Payment Flow

```typescript
// 1. Create SPT with tight constraints
const spt = await stripe.sharedPayment.grantedTokens.create({
  payment_method: "pm_xxx",
  usage_limits: {
    currency: "usd",
    max_amount: 800,        // $8.00
    expires_at: now + 300,  // 5 minutes
  },
  seller_details: {
    network_id: "linear",   // merchant identifier
  },
});

// 2. Use SPT to create PaymentIntent
const pi = await stripe.paymentIntents.create({
  amount: 800,
  currency: "usd",
  shared_payment_granted_token: spt.id,
  confirm: true,
  metadata: {
    source: "agent-commerce-cli",
    merchant: "Linear",
  },
});
```

### c) ACP Merchant Integration (Future)

For merchants implementing the full ACP protocol, agent-pay would interact with their checkout endpoints directly:

```
POST /acp/checkout/create    → Create checkout session
POST /acp/checkout/update    → Set shipping, apply SPT
POST /acp/checkout/complete  → Finalize purchase
```

This requires merchants to implement ACP endpoints, which is a broader ecosystem dependency.

## 2. MCP Service Discovery

### Current: Simulated Registry

agent-pay includes a local service catalog with demo entries (Linear, Asana, GitHub Copilot). Each entry includes:

```typescript
interface ServiceListing {
  name: string;
  slug: string;
  description: string;
  pricing: {
    amount: number;     // cents
    currency: string;
    interval: "month" | "y

*[truncated — see source for full prompt]*