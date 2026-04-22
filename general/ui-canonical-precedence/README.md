# UI CANONICAL PRECEDENCE

> This document resolves conflicting UI guidance across legacy repo docs, AGENTS guidance, and LIC references.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UI Canonical Precedence (Phase-0 Lock)

This document resolves conflicting UI guidance across legacy repo docs, AGENTS guidance, and LIC references.

## Scope

- Applies to product application UI under `apps/web/**`.
- Excludes marketing-site visuals and interactions.
- Treat the Brand Identity "standards manual app" as a documentation container, not as product UX to clone.

## Canonical Source Order

1. `lic-design-system/references/interaction-and-ai.md`
2. `lic-design-system/references/ui-kit.md`
3. `lic-design-system/references/design-tokens.md`
4. `lic-design-system/references/source-map.md`
5. Legacy local docs (`brand/**`, `uirefactorprompt.md`, prior superseded `docs/UI_*.md`) are archive-only and non-canonical.
6. `AGENTS.md` / `agents.md` remain execution constraints and must stay aligned with this precedence contract for UI values.

If a rule conflicts, higher-order source wins.

## Conflict Decisions

### Color profile

- Canonical product palette uses the LIC reference profile:
  - Paper `#F7F5F0`
  - Ink `#0B0B0B`
  - Institutional `#2B4C7E`
  - Filing Red `#8B2500`
  - Ledger `#2D5F3A`
- Legacy palette values are treated as transitional and must not be reintroduced.

### Typography

- Body copy: IBM Plex Sans.
- Labels, metadata, status, table headers: IBM Plex Mono (uppercase where applicable).
- Page/module headings: IBM Plex Sans Condensed uppercase with tracked letter spacing.
- This split preserves procedural readability and resolves mono-vs-condensed conflict without adding new font families.

### Branding compatibility boundary (Decision 1A, closed)

- `KAR-76` completed LIC naming/logo migration for product-facing surfaces.
- Compatibility identifiers may remain only in non-UI/runtime compatibility surfaces:
  - package/repo identifiers (for example `karen-legal-suite`)
  - legacy integration headers (`x-karen-*`) where backward compatibility is required
- New UI copy and all user-facing identity surfaces must use LIC naming.

### Standards-

*[truncated — see source for full prompt]*