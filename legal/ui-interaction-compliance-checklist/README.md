# UI INTERACTION COMPLIANCE CHECKLIST

> Source of truth: `lic-design-system/references/`
Canonical component matrix: `lic-design-system/references/ui-kit.md`
Canonical precedence contract: `

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UI + Interaction Compliance Checklist

Source of truth: `lic-design-system/references/`
Canonical component matrix: `lic-design-system/references/ui-kit.md`
Canonical precedence contract: `docs/UI_CANONICAL_PRECEDENCE.md`
Explicitly out of scope for product app parity: `lic-design-system/references/marketing-site.md`.

Use this checklist for any UI-affecting ticket or PR.

## 1) Visual System
- Uses canonical palette only (`Paper #F7F5F0`, `Ink #0B0B0B`, `Institutional #2B4C7E`, `Filing Red #8B2500`, `Ledger #2D5F3A`, tokenized neutrals).
- No gradients.
- No shadows.
- No rounded corners.
- Border/rule-based hierarchy present.

## 2) Typography + Copy
- Condensed used for headings (`uppercase`, tracking `0.06em`).
- Mono used for labels/codes/status metadata.
- Sans used for body content.
- Serif used sparingly for approved emphasis contexts only.
- Voice is procedural and terse.
- No hype/friendly filler phrases.
- Product copy does not include standards-manual scaffolding markers (`Standards Manual`, `LIC / IDENTITY`, revision/confidential banner language).

## 3) Layout + Density
- 12-column desktop structure respected.
- Responsive matrix enforced:
  - `>=1280px` full desktop layout with visible sidebar and full-width tables.
  - `1024-1279px` compact desktop (collapsed rail/hamburger, dense-data readability preserved via scroll where needed).
  - `768-1023px` tablet mode (overlay navigation drawer, single-column content, 48px touch targets).
  - `<768px` unsupported notice shown with predictable fallback behavior.
- 8px spacing scale respected.
- Table/list-first for dense operational data.
- Max content width and margin constraints respected.

## 4) Interaction Behavior
- State is always visible.
- Destructive or irreversible actions require explicit confirmation.
- System does not interrupt first (no unsolicited intrusive modals/tooltips).
- Motion is functional and linear only.
- No anti-patterns: infinite scroll, skeleton shimmer, optimistic critical wri

*[truncated — see source for full prompt]*