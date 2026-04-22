# VALIDATION CHECKLIST

> Complete pre-deployment and go-live validation checklist for Pact Marketplace.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Validation Checklist

Complete pre-deployment and go-live validation checklist for Pact Marketplace.

---

## Phase 1: Code Quality Validation

### TypeScript & Linting

- [ ] No TypeScript errors: `npm run build` passes
- [ ] No ESLint warnings: `npx eslint src/` clean
- [ ] No console.errors or warnings in browser console
- [ ] All imports resolved correctly
- [ ] No unused imports or variables

**Command:**
```bash
npm run build && npx eslint src/ --max-warnings 0
```

### Unit Tests

- [ ] All unit tests passing: `npm test` ✅
- [ ] Test coverage > 80% for critical paths
- [ ] No failing tests for:
  - [ ] Payment verification
  - [ ] Pool operations
  - [ ] Admin APIs
  - [ ] Contact submissions

**Command:**
```bash
npm test -- --coverage --testPathPattern="(payment|pool|admin|contact)"
```

### Code Coverage

- [ ] src/services/pact.service.ts: > 90% coverage
- [ ] src/services/payment.service.ts: > 90% coverage
- [ ] src/app/api/payments/: > 85% coverage
- [ ] src/app/api/admin/: > 85% coverage

**Command:**
```bash
npm test -- --coverage --collectCoverageFrom="src/**/*.{ts,tsx}"
```

---

## Phase 2: Database Validation

### Schema Integrity

- [ ] All tables exist:
  - [ ] `profiles` table present
  - [ ] `listings` table present
  - [ ] `pools` table present
  - [ ] `pool_members` table present
  - [ ] `orders` table present
  - [ ] `payouts` table present
  - [ ] `contact_submissions` table present

**SQL:**
```sql
SELECT table_name FROM information_schema.tables 
WHERE table_schema = 'public' ORDER BY table_name;
```

### Columns & Data Types

- [ ] `payouts` table has required columns:
  - [ ] `id` (uuid, primary key)
  - [ ] `user_id` (uuid, foreign key to profiles)
  - [ ] `pool_id` (uuid, foreign key to pools)
  - [ ] `listing_id` (uuid, foreign key to listings)
  - [ ] `farmer_id` (uuid)
  - [ ] `amount` (bigint, kobo)
  - [ ] `reference` (varchar, unique)
  - [ ] `stat

*[truncated — see source for full prompt]*