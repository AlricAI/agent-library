# UI TOKEN CONTRACT

> ## Canonical Source and Precedence

- Canonical precedence is defined in `docs/UI_CANONICAL_PRECEDENCE.md`.
- Product UI tokens and interaction consta

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# KAR-55 UI Token Contract

## Canonical Source and Precedence

- Canonical precedence is defined in `docs/UI_CANONICAL_PRECEDENCE.md`.
- Product UI tokens and interaction constants must follow:
  1. `lic-design-system/references/interaction-and-ai.md`
  2. `lic-design-system/references/ui-kit.md`
  3. `lic-design-system/references/design-tokens.md`
  4. `lic-design-system/references/source-map.md` (traceability to original manual sections)
- Product app scope excludes `lic-design-system/references/marketing-site.md`.
- Standards-manual app shell/routing (`brand/Brand Identity Document*/src/app/components/Layout.tsx`, `src/app/routes.ts`) are documentation UX and not canonical product layout/copy sources.

## Color Tokens (Fixed Palette)

### Primary
- `--lic-ink`: `#0B0B0B`
- `--lic-paper`: `#F7F5F0`

### Neutrals
- `--lic-graphite`: `#3A3A3A`
- `--lic-slate`: `#6B6B6B`
- `--lic-silver`: `#A8A8A8`
- `--lic-fog`: `#D4D2CD`
- `--lic-parchment`: `#ECEAE4`

### Functional
- `--lic-institutional`: `#2B4C7E` (links, active, focus)
- `--lic-filing-red`: `#8B2500` (destructive, errors)
- `--lic-ledger`: `#2D5F3A` (success/approval)

Rule: do not introduce ad hoc colors outside the token set.

## Typography Tokens

- `--lic-font-condensed`: IBM Plex Sans Condensed (page/module headings, uppercase + 0.06em tracking)
- `--lic-font-sans`: IBM Plex Sans (body/help/prose)
- `--lic-font-mono`: IBM Plex Mono (labels/metadata/codes/status/table headings)

### Role Mapping
- Route/page headings and section titles -> Condensed
- Body/descriptions/form help -> Sans
- Labels/codes/audit metadata/status/table headers -> Mono

## Spacing + Grid Tokens

### Base scale
- 8px base: `4, 8, 16, 24, 32, 48, 64, 96`

### Layout doctrine
- 12-column desktop layout.
- Max content width `960px` for dense procedural surfaces.
- Horizontal margins never below `32px`.

### Responsive behavior doctrine
- `>=1280px`: full desktop shell, persistent sidebar, dense table-first layouts.
- `1024-1279px`: co

*[truncated — see source for full prompt]*