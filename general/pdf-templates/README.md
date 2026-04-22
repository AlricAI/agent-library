# Pdf Templates

> [← Back to Index](./index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tech Invoice Forge - PDF Templates

[← Back to Index](./index.md) | [Master Plan](./master-plan.md) | [UI/UX Design](./ui-ux.md)

---

## Template Overview

Tech Invoice Forge offers four professionally designed invoice templates. Each template is implemented as a pdfmake document definition function.

---

## Template Comparison

| Template    | Style          | Best For          | Character                  |
| :---------- | :------------- | :---------------- | :------------------------- |
| **Modern**  | Clean, minimal | General use       | Contemporary, professional |
| **Classic** | Traditional    | Corporate clients | Formal, established        |
| **Tech**    | Code-inspired  | Developer clients | Technical, distinctive     |
| **Compact** | Dense layout   | Many line items   | Efficient, detailed        |

---

## 1. Modern Template (Default)

### Description

Clean, contemporary design with generous whitespace and subtle typography hierarchy.

### Visual Structure

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│  [LOGO]                                              INVOICE    │
│  Acme Development LLC                               INV-2026-001│
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FROM                              BILL TO                      │
│  Acme Development LLC              John Smith                   │
│  123 Tech Lane                     TechStartup Inc              │
│  San Francisco, CA 94105           456 Innovation Blvd          │
│  billing@acmedev.com               New York, NY 10001           │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  Issue Date: Feb 1, 2026    Due Date: Mar 3, 2026  

*[truncated — see source for full prompt]*