# MAILERSEND TEMPLATES

> When you build each template in the MailerSend dashboard, use **exactly** the variable names below.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MailerSend Template Variable Schema

When you build each template in the MailerSend dashboard, use **exactly** the variable names below. The runtime sends them via the personalization API in the format MailerSend expects (snake_case keys, Twig syntax in the editor: `{$first_name}`, `{% for item in items %}…{% endfor %}`).

Once a template is built, paste its ID into the matching env var (Vercel → Settings → Environment Variables). When the env var is present, our code switches that send from inline HTML to the MailerSend template; when absent, it falls back to the inline HTML version we already render.

| Template (file) | Env var | Tag |
|---|---|---|
| order-confirmed | `MAILERSEND_TEMPLATE_ORDER_CONFIRMED` | `transactional/order-confirmed` |
| order-label-printed | `MAILERSEND_TEMPLATE_ORDER_LABEL_PRINTED` | `transactional/order-label-printed` |
| order-packed | `MAILERSEND_TEMPLATE_ORDER_PACKED` | `transactional/order-packed` |
| order-shipped | `MAILERSEND_TEMPLATE_ORDER_SHIPPED` | `transactional/order-shipped` |
| order-delivered | `MAILERSEND_TEMPLATE_ORDER_DELIVERED` | `transactional/order-delivered` |
| abandoned-cart | `MAILERSEND_TEMPLATE_ABANDONED_CART` | `marketing/abandoned-cart` |
| promotional | `MAILERSEND_TEMPLATE_PROMOTIONAL` | `marketing/promotional` |
| reorder-reminder | `MAILERSEND_TEMPLATE_REORDER_REMINDER` | `marketing/reorder-reminder` |
| new-account-welcome | `MAILERSEND_TEMPLATE_WELCOME` | `transactional/welcome` |
| new-account-onboarding | `MAILERSEND_TEMPLATE_ONBOARDING` | `transactional/onboarding` |
| password-reset | `MAILERSEND_TEMPLATE_PASSWORD_RESET` | `transactional/password-reset` |

---

## Variable schema per template

Every template gets these **shared** variables for the legal footer (don't surface them in the body, just leave them available):

```
legal_company         = "Hilxera Distribution Services LLC"
legal_filing_id       = "2026-001928701"
legal_filing_url      = "https://wyobiz.wyo.gov/business/FilingDetails.asp

*[truncated — see source for full prompt]*