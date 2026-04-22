# E2E TEST SCENARIOS

> Comprehensive E2E test flows for validating the complete Pact Marketplace workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# End-to-End Test Scenarios

Comprehensive E2E test flows for validating the complete Pact Marketplace workflows.

## Prerequisites

- Supabase project configured with all migrations applied
- Paystack sandbox credentials configured
- Admin and farmer accounts created
- Buyer account created
- At least one pool and listing created

---

## Scenario 1: Complete Pool Lifecycle

**Goal:** Validate full pool lifecycle from creation to payout

### Steps

1. **Create Pool (Farmer)**
   - Navigate to `/farmer` → "Create Pool"
   - Fill form:
     - Listing: Select existing listing
     - Min Quantity: 50
     - Max Quantity: 200
     - Expiry: 7 days from now
   - Click "Create Pool"
   - **Expected:** Pool created, status = "active", page redirects to pool details

2. **Join Pool (Buyer 1)**
   - Navigate to `/marketplace`
   - Find the created pool
   - Click "Join Pool"
   - Enter quantity: 30
   - Click "Pay with Paystack"
   - Complete payment (use sandbox card: 4111 1111 1111 1111)
   - **Expected:** Redirect to success page, pool_members entry created with payment_status="authorized"

3. **Join Pool (Buyer 2)**
   - Repeat as different buyer with quantity: 25
   - **Expected:** Pool current_quantity = 55, pool_members count = 2

4. **Wait for Auto-Lock**
   - Wait 5 minutes for cron job to run
   - Check Supabase: pools.status should change to "locked"
   - **Expected:** status = "locked", process_pool_lock RPC executed successfully

5. **Verify Orders Created**
   - Query database: `SELECT * FROM orders WHERE pool_id = '<pool_id>'`
   - **Expected:** 2 orders created (one per member), status = "confirmed", amount matches pledged

6. **Verify Inventory Deducted**
   - Query listing: `SELECT quantity FROM listings WHERE id = '<listing_id>'`
   - **Expected:** quantity decreased by 55 (sum of all pledges)

7. **Verify Payout Generated**
   - Query payouts: `SELECT * FROM payouts WHERE pool_id = '<pool_id>'`
   

*[truncated — see source for full prompt]*