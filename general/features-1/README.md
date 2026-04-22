# Features

> [← Back to Index](./index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tech Invoice Forge - Features

[← Back to Index](./index.md) | [Master Plan](./master-plan.md) | [Architecture](./architecture.md)

---

## Feature Overview

This document provides detailed specifications for all features in Tech Invoice Forge. Features are organized by priority and implementation phase.

---

## Phase 1: Core MVP

### 1.1 Invoice Form

#### Sender Information Section

**Fields:**
| Field | Type | Required | Validation | Notes |
| :------------ | :------- | :------- | :--------------------- | :------------------------------- |
| Business Name | Text | Yes | 1-100 chars | Displayed prominently on invoice |
| Address | Textarea | Yes | 5-500 chars | Multi-line, preserves formatting |
| Email | Email | Yes | Valid email format | Contact email on invoice |
| Phone | Tel | No | E.164 format preferred | Optional contact |
| Tax ID / VAT | Text | No | 1-50 chars | For tax compliance |
| Logo | File | No | PNG, JPG, SVG; max 2MB | Displayed on invoice header |

**Behavior:**

- Auto-saves to IndexedDB when field loses focus
- Loads automatically on return visits
- "Clear" button resets all fields
- Logo preview with remove option

---

#### Client Information Section

**Fields:**
| Field | Type | Required | Validation | Notes |
| :---------- | :------- | :------- | :----------------- | :---------------------------- |
| Client Name | Text | Yes | 1-100 chars | Individual or business name |
| Company | Text | No | 1-100 chars | If different from client name |
| Address | Textarea | Yes | 5-500 chars | Billing address |
| Email | Email | Yes | Valid email format | For records |

**Features:**

- **Client Selector**: Dropdown to select from saved clients
- **Quick Add**: Save current client to address book
- **Edit Client**: Modify existing saved client

---

#### Invoice Details Section

**Fields:**
| Field | Type | Required | Default | Notes |
| :------------- | :----- | :------- | :-------------- | :------------------------------------------------------ |


*[truncated — see source for full prompt]*