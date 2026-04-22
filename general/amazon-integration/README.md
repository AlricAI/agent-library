# Amazon Integration

> This document describes how the Amazon Reviews integration works in Reese Reviews, including how to use demo mode, how to set up cookie-based live import, and privacy considerations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Amazon Reviews Integration

This document describes how the Amazon Reviews integration works in Reese Reviews, including how to use demo mode, how to set up cookie-based live import, and privacy considerations.

---

## Overview

The integration allows you to import your Amazon Vine and/or purchase reviews into the app, display them as anonymised drafts, and publish or copy them into your review workflow.

All imported reviews are displayed **without your Amazon reviewer handle** — only the product name, star rating, and review text are shown.

---

## 1. Demo Mode (default)

Demo mode is active automatically when no `AMAZON_SESSION_COOKIE` is present. It loads five pre-built sample reviews that showcase all UI features without any credentials.

**To trigger demo mode via the UI:**

1. Go to **Business Dashboard → 🛒 Amazon → Connection tab**.
2. Select **Demo** mode.
3. Click **Import Reviews**.
4. Switch to the **Reviews tab** to see the imported reviews.

---

## 2. HTML Import Mode

HTML mode is a safe, credential-free alternative to the live cookie scraper. You paste the raw HTML source of your Amazon review page and the app parses it client-side.

**Steps:**

1. Log in to [amazon.com](https://www.amazon.com) and navigate to **Your Account → Your Amazon profile → Community → See all reviews**.
2. Right-click the page → **View Page Source** (or `Ctrl+U` / `Cmd+U`).
3. Select all (`Ctrl+A`) and copy the HTML.
4. In the app, go to **Business Dashboard → 🛒 Amazon → Connection → Paste HTML** mode.
5. Paste the HTML into the text area and click **Import Reviews**.

The parser tolerates minor differences in Amazon's HTML structure across locales and page versions. If no reviews are found, ensure you copied from a page that contains review blocks (`data-hook="review"` or `.review` elements).

---

## 3. Cookie Mode (server-side scraper)

Cookie mode uses an active Amazon session cookie to fetch your review pages server-side and scrape review data. Because cookies ar

*[truncated — see source for full prompt]*