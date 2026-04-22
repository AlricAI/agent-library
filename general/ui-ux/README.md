# Ui Ux

> [← Back to Index](./index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tech Invoice Forge - UI/UX Design

[← Back to Index](./index.md) | [Master Plan](./master-plan.md) | [Branding](./branding.md)

---

## Design Philosophy

### Core Principles

1. **Functional Minimalism** - Every element serves a purpose
2. **Professional Aesthetics** - Mature, trustworthy appearance
3. **Speed** - Minimal clicks to complete tasks
4. **Mobile-First** - Responsive design from the ground up
5. **Accessibility** - WCAG 2.1 AA compliance

### Visual Language

- **No gradients** - Flat, solid colors only
- **Subtle shadows** - For depth and hierarchy
- **Generous spacing** - Breathable, not cramped
- **Consistent radius** - 8px (var(--radius)) everywhere

---

## Layout Structure

### Main Application Layout

```
┌─────────────────────────────────────────────────────────────────┐
│ Header: Logo | Theme Toggle | Export | Settings                 │
├────────────────────────────────┬────────────────────────────────┤
│                                │                                │
│       Invoice Form             │       Preview Panel            │
│       (Scrollable)             │       (Fixed/Sticky)           │
│                                │                                │
│   ┌──────────────────────┐    │   ┌────────────────────────┐   │
│   │ Sender Section       │    │   │                        │   │
│   └──────────────────────┘    │   │                        │   │
│   ┌──────────────────────┐    │   │    PDF Preview         │   │
│   │ Client Section       │    │   │    (Live Update)       │   │
│   └──────────────────────┘    │   │                        │   │
│   ┌──────────────────────┐    │   │                        │   │
│   │ Invoice Details      │    │   │                        │   │
│   └──────────────────────┘    │   │                        │   │
│   ┌──────────────────────┐    │   └────────────────────────┘   │
│   │ Line Items           │    │                                │
│   └──────────────────────┘    │   ┌─────────────

*[truncated — see source for full prompt]*