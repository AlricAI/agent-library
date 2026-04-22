# Ui Design Spec

> This doc is the single source of truth for UI styling.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agentron Studio — UI Design Spec

This doc is the single source of truth for UI styling. When adding or changing CSS (e.g. in `packages/ui/app/globals.css`), use these tokens and scales so the app stays consistent.

---

## 1. Design tokens (CSS variables)

All colors and key surfaces must use these variables. Do not introduce new hex/rgba values for background, text, or primary actions.

### Light (`:root`)

| Token | Value | Use |
|-------|--------|-----|
| `--bg` | `#f5f6fa` | Page background |
| `--surface` | `#ffffff` | Cards, panels, topbar |
| `--surface-muted` | `#f1f5f9` | Inputs, list items, muted blocks |
| `--text` | `#0f172a` | Primary text |
| `--text-muted` | `#64748b` | Secondary text, labels |
| `--primary` | `#5b7cfa` | Primary actions, links, active state |
| `--primary-strong` | `#4f46e5` | Gradient end, emphasis |
| `--border` | `rgba(148, 163, 184, 0.25)` | Borders, dividers |
| `--shadow` | `0 24px 60px rgba(15, 23, 42, 0.08)` | Cards, panels |
| `--sidebar-bg` | `#ffffff` | Sidebar background |
| `--sidebar-text` | `#0f172a` | Sidebar text |
| `--sidebar-text-muted` | `#64748b` | Sidebar secondary |
| `--sidebar-hover` | `rgba(15, 23, 42, 0.06)` | Nav hover |
| `--sidebar-active` | `rgba(91, 124, 250, 0.12)` | Nav active bg |
| `--sidebar-active-border` | `rgba(91, 124, 250, 0.3)` | Nav active border |

### Dark (`html[data-theme="dark"]`)

Same token names; values are defined in `globals.css` (darker backgrounds, lighter text, adjusted shadows). Always use the variable names, never hardcode light/dark values in component CSS.

### Optional (add to globals if needed)

- `--resource-green` — e.g. `#22c55e` for low usage
- `--resource-yellow` — e.g. `#eab308` for medium
- `--resource-red` — e.g. `#ef4444` for high

---

## 2. Spacing and sizing scale

Use this scale for padding, gap, margin, and border-radius so the UI feels consistent.

| Name | Value | Typical use |
|------|--------|-------------|
| xs | 0.25rem (4px) | Tight gaps, icon pad

*[truncated — see source for full prompt]*