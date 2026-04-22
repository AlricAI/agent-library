# SIDEBAR PATTERN

> Cross-reference: See `AGENTS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sidebar Pattern Specification
Cross-reference: See `AGENTS.md` → `Layout Invariants (MUST)` for global layout and layering constraints that apply alongside this sidebar spec.

## Overview

The app uses a **global collapsible sidebar** with two stable states:
- **Expanded**: Icons + labels (240px width)
- **Collapsed**: Icons only (72px width)

This pattern applies to all navigation and sidebar components throughout the application. The spec prevents UI drift and ensures consistent user experience across pages.

---

## 1. Behavior Rules (MUST)

### 1.1 — Global State

- **Sidebar state is global**, not per-page
- **localStorage key**: `sidebar:collapsed` (boolean: `true` or `false`)
- Persists across browser sessions
- Applied on initial app load (hydrate before first render)
- No layout flicker on load (hydrate early in layout component)

**Implementation**:
```typescript
// src/hooks/useSidebarState.ts
const [collapsed, setCollapsed] = useLocalStorage('sidebar:collapsed', false);
```

### 1.2 — Layout Response

- Sidebar must **resize content, not overlay it**
- **Expanded state**: sidebar width `240px`
- **Collapsed state**: sidebar width `72px`
- Content remains in a sibling layout column and shifts naturally with sidebar width changes
- No floating drawer behavior
- Content shifts predictably with sidebar width
- Prevents layout instability and maintains readable content area

### 1.3 — Transition Timing

- **Duration**: 200ms
- **Easing**: `ease-in-out`
- Apply transitions to:
  - Sidebar width
  - Sidebar-adjacent layout changes when animated
- Do NOT animate individual items, labels, or icons
- Keep animation smooth but not distracting
- If toggle occurs while keyboard focus is inside sidebar, focus must remain predictable (preserve current focus if valid, otherwise move to sidebar toggle; never drop to page body)
- Reduced-motion requirement: when `prefers-reduced-motion` is active, disable sidebar/nav/toggle transitions (`motion-reduce:transition-none`) 

*[truncated — see source for full prompt]*