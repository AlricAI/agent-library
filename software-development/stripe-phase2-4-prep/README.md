# Stripe Phase2 4 Prep

> **Date:** 2026-03-15  
**Status:** Ready for Miles' Stripe account setup  
**Next:** Phase 2 (Backend) → Phase 3 (Webhook) → Phase 4 (Testing)

---

#

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Stripe Phase 2-4 Preparation

**Date:** 2026-03-15  
**Status:** Ready for Miles' Stripe account setup  
**Next:** Phase 2 (Backend) → Phase 3 (Webhook) → Phase 4 (Testing)

---

## Phase 2: Backend PaymentIntent Endpoint

### Node.js Implementation (Express)

```javascript
// server.js - PaymentIntent endpoint
const express = require('express');
const stripe = require('stripe')(process.env.STRIPE_SECRET_KEY);
const app = express();

app.use(express.json());

// Create PaymentIntent
app.post('/api/create-payment-intent', async (req, res) => {
  try {
    const { amount, currency = 'usd', metadata = {} } = req.body;
    
    // Validate amount
    if (!amount || amount < 50) { // Minimum 50 cents
      return res.status(400).json({ error: 'Invalid amount' });
    }
    
    const paymentIntent = await stripe.paymentIntents.create({
      amount: amount, // Amount in cents
      currency: currency,
      automatic_payment_methods: { enabled: true },
      metadata: {
        ...metadata,
        created_at: new Date().toISOString(),
      },
    });
    
    res.json({
      clientSecret: paymentIntent.client_secret,
      paymentIntentId: paymentIntent.id,
    });
  } catch (error) {
    console.error('PaymentIntent error:', error);
    res.status(500).json({ error: error.message });
  }
});

// Retrieve PaymentIntent status
app.get('/api/payment-intent/:id', async (req, res) => {
  try {
    const paymentIntent = await stripe.paymentIntents.retrieve(req.params.id);
    res.json({
      status: paymentIntent.status,
      amount: paymentIntent.amount,
      currency: paymentIntent.currency,
      metadata: paymentIntent.metadata,
    });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

const PORT = process.env.PORT || 4242;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

### Python Implementation (Flask)

```python
# app.py - PaymentIntent endpoint
from flask import Flask, request, jsonify
import stripe
im

*[truncated — see source for full prompt]*