---
name: MAILERSEND TEMPLATES
description: When you build each template in the MailerSend dashboard, use **exactly** the variable names below.
model: claude-sonnet-4-5
---
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
legal_filing_url      = "https://wyobiz.wyo.gov/business/FilingDetails.aspx?eFNum=…"
support_email         = "hello@new-u.io"
site_url              = "https://new-u.io"
```

### `order-confirmed`
```
first_name            "Maya"
order_ref             "NUP-4F8K2Q91"
order_date            "2026-04-15"      (ISO 8601 date)
total                 "284.00"
currency              "USD"
order_url             "https://new-u.io/account/orders"
items                 [
  { name: "BPC-157 — 5mg — (10 vial pack)", quantity: 1, unit_price: "120.00", line_total: "120.00" },
  { name: "TB-500 — 10mg",                  quantity: 2, unit_price: "72.00",  line_total: "144.00" }
]
shipping_name         "Maya Patel"
shipping_line1        "221B Baker Street"
shipping_line2        "Apt 4"            (may be empty string)
shipping_city         "London"
shipping_state        ""                 (may be empty)
shipping_postcode     "NW1 6XE"
shipping_country      "United Kingdom"
```

### `order-label-printed` / `order-packed`
```
first_name            "Maya"
order_ref             "NUP-4F8K2Q91"
```

### `order-shipped`
```
first_name             "Maya"
order_ref              "NUP-4F8K2Q91"
order_url              "https://new-u.io/account/orders"
tracking_number        "1Z999AA10123456784"
carrier                "UPS"
tracking_url           "https://www.ups.com/track?tracknum=1Z999AA10123456784"
expected_arrival_from  "2026-04-18T20:47:02.872Z"   (ISO 8601)
expected_arrival_until "2026-04-29T20:47:02.872Z"   (ISO 8601)
total                  "284.00"
currency               "USD"
items                  [ { name, quantity, unit_price, line_total }, … ]
shipping_name          "Maya Patel"
shipping_line1         "221B Baker Street"
shipping_city          "London"
shipping_postcode      "NW1 6XE"
shipping_country       "United Kingdom"
```

### `order-delivered`
```
first_name            "Maya"
order_ref             "NUP-4F8K2Q91"
total                 "284.00"
currency              "USD"
items                 [ { name, quantity, unit_price, line_total }, … ]
shipping_name         …
shipping_line1        …
shipping_city         …
shipping_postcode     …
shipping_country      …
```

### `abandoned-cart`
```
first_name            "Maya"
cart_subtotal         "264.00"
recovery_url          "https://new-u.io/cart/recover/<token>"
discount_code         "COMEBACK15-AB12C"
discount_label        "15% off your full cart — expires in 48 hours"
expires_at            "2026-04-17T12:30:00Z"   (ISO 8601)
items                 [ { name: "BPC-157 5mg (10 vial pack)", quantity: 1, line_total: "120.00" }, … ]
```

### `promotional`
```
first_name            "Maya"
headline              "Spring restock — 20% off BPC-157 + TB-500 stack"
body_html             "<p>New batch just landed…</p>"   (raw HTML, render with `{{ body_html | raw }}`)
cta_label             "Shop the stack"
cta_url               "https://new-u.io/stacks/healing-stack"
promo_code            "SPRING20"        (optional — may be empty string)
promo_meta            "20% off · expires Sunday"
```

### `reorder-reminder`
```
first_name            "Maya"
order_ref             "NUP-4F8K2Q91"   (the previous order)
discount_code         "WELCOME20-AB12C"
shop_url              "https://new-u.io/shop"
```

### `new-account-welcome`
```
first_name            "Maya"
account_url           "https://new-u.io/account"
```

### `new-account-onboarding`
```
first_name            "Maya"
shop_url              "https://new-u.io/shop"
```

### `password-reset`
```
first_name            "Maya"
reset_link            "https://new-u.io/account/reset-password?token=<64hex>"
expires_in            "1 hour"
```

---

## How to write loops in the MailerSend editor

Items arrays use Twig syntax. For order-confirmed:

```twig
{% for item in items %}
  <tr>
    <td>{{ item.name }}</td>
    <td>×{{ item.quantity }}</td>
    <td>${{ item.line_total }}</td>
  </tr>
{% endfor %}
```

For abandoned-cart:

```twig
<ul>
  {% for item in items %}
    <li>{{ item.name }} × {{ item.quantity }}{% if item.line_total %} — ${{ item.line_total }}{% endif %}</li>
  {% endfor %}
</ul>
```

---

## Recommended template structure (copy from /email-templates previews)

The HTML files in this directory render the current cyan-purple/dark frame layout. Copy the structure into the MailerSend editor and replace the hardcoded values with `{$variable}` placeholders.

For the gradient first-name highlight inside greetings, wrap the variable in:

```html
<span style="background:linear-gradient(135deg,#22d3ee 0%,#a855f7 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;color:#a78bfa;font-weight:700">{$first_name}</span>
```

For solid-green CTA buttons:

```html
<a href="{$cta_url}" style="display:inline-block;background:#39ff14;color:#0c1118;font-weight:700;font-size:14px;padding:14px 34px;border-radius:6px;text-decoration:none;text-transform:uppercase">{$cta_label}</a>
```

The legal footer always closes the email — paste this verbatim:

```html
<p style="margin:12px 0 0;font-size:11px;color:#6b7a8d;line-height:1.6">
  New-U Peptides is a brand operated by
  <a href="{$legal_filing_url}" style="color:#6b7a8d;text-decoration:underline">{$legal_company}</a>,
  a limited liability company registered in the State of Wyoming, USA · Filing ID: {$legal_filing_id}.
</p>
```