# LEDGER DOMAIN

> ## Canonical Ledger Events

The application must treat these as the economic source of truth:

- `income`: money entering an account.
- `expense_cash`

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Ledger Domain And Calculation Matrix

## Canonical Ledger Events

The application must treat these as the economic source of truth:

- `income`: money entering an account.
- `expense_cash`: immediate expense paid from an account.
- `card_purchase`: economic expense created by a credit-card purchase.
- `installment_due`: monthly economic portion of a parcelled card purchase.
- `invoice_payment`: settlement of card liability, not a new monthly expense.
- `transfer`: internal movement between accounts, neutral for income/expense totals.
- `investment_contribution`: money moved from account cash into invested assets.
- `investment_withdrawal`: money moved from invested assets back into account cash.
- `reimbursement_expected`: amount expected back from a third party.
- `reimbursement_received`: reimbursement actually received.
- `manual_adjustment`: explicit corrective entry when needed.

## Domain Rules

- Dashboard, History, Cards, Reports and Planning must all be explainable from ledger events plus deterministic projections.
- `invoice_payment` never increases monthly expense totals.
- Card purchases are economic expenses at purchase time; invoice payment only settles liability.
- Parcelled purchases must keep parent-child traceability: purchase -> installments -> invoice item -> invoice payment.
- Transfers are operational events and must not distort income or expense totals.
- Reimbursements must preserve person linkage and status.

## Credit Card Glossary

- `purchase`: the original credit-card buying event. It owns description, category, card and total amount.
- `installment`: one economic monthly slice derived from a parcelled purchase. It keeps the link to the parent purchase and target invoice.
- `invoice`: the operational billing cycle for a card in a reference month.
- `invoice item`: the installment row that composes a specific invoice.
- `invoice payment`: settlement of the card liability from an account. It reduces invoice balance and card liability, bu

*[truncated — see source for full prompt]*