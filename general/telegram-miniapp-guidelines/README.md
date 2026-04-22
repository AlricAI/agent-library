# TELEGRAM MINIAPP GUIDELINES

> Implementation-ready guidelines for building production Telegram Mini Apps.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Telegram Mini App Guidelines — Production Spec

Implementation-ready guidelines for building production Telegram Mini Apps. Practical, specific, actionable for designers and engineers.

**References:** [core.telegram.org/bots/webapps](https://core.telegram.org/bots/webapps)

---

## Table of contents

1. [Platform overview](#1-platform-overview)
2. [UX rules & patterns](#2-ux-rules--patterns)
3. [UI system rules (design tokens)](#3-ui-system-rules-design-tokens)
4. [Navigation & page architecture](#4-navigation--page-architecture)
5. [Telegram WebApp API integration](#5-telegram-webapp-api-integration)
6. [Theming](#6-theming)
7. [Performance & reliability](#7-performance--reliability)
8. [Security & privacy](#8-security--privacy)
9. [Analytics & logging](#9-analytics--logging)
10. [QA checklist & acceptance criteria](#10-qa-checklist--acceptance-criteria)
11. [Anti-patterns](#11-anti-patterns)
12. [Example reference flows](#12-example-reference-flows)

---

## 1. Platform overview

### Where Mini App lives

- **Launch modes:** Main Mini App, menu button, inline button, keyboard button, direct link, attachment menu
- **Viewport:** Half-screen by default; expandable to full via `expand()` or user drag
- **Desktop:** Same codebase; larger viewport; keyboard/mouse instead of touch

### Mobile-first reality

- 80%+ users on mobile
- Design for thumb reach; primary actions in lower half
- Desktop Telegram: same WebView; wider layout, hover states

### Safe areas / insets

- **System safe area:** `--tg-safe-area-inset-top`, `--tg-safe-area-inset-bottom`, `--tg-safe-area-inset-left`, `--tg-safe-area-inset-right` (Bot API 8.0+)
- **Content safe area:** `--tg-content-safe-area-inset-*` for overlap with Telegram UI
- **Bottom nav:** `padding-bottom: env(safe-area-inset-bottom, 0)`
- **Header:** `padding-inline: calc(var(--space-4) + env(safe-area-inset-left, 0))`

### Keyboard behavior

- Use `hideKeyboard()` (Bot API 9.1+) when appropriate
- Avoid layout jump: fixed/sticky

*[truncated — see source for full prompt]*