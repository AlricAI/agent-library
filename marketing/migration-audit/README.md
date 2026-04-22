# MIGRATION AUDIT

> Read-only audit of the current `sighthound-content-ops` app against `design-system/`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sighthound Content Relay — Migration Audit (Phase 0)

Read-only audit of the current `sighthound-content-ops` app against `design-system/`.
No code changes made.

Commit baseline: `baaf298` on `main` (post-flashpoint; `design-system/` committed in `3d18a65`).

---

## 1. Current stack

| Layer | What is actually in use |
|---|---|
| Framework | Next.js **15.3.8**, App Router (`src/app/`), React 18.3.1 |
| CSS approach | **Tailwind CSS v4** (via `@tailwindcss/postcss` 4.2.2) |
| Tailwind config | **No `tailwind.config.ts` / .js** — v4 uses CSS-first `@theme inline` in `src/app/globals.css` |
| Component library | **None.** Custom primitives under `src/components/` (`button.tsx`, `data-table.tsx`, `detail-drawer.tsx`, `confirmation-modal.tsx`, etc.) |
| Icon set | `lucide-react` **0.577.0** via shared wrapper `src/lib/icons.tsx` (`AppIcon` + per-icon exports at 1.75 stroke weight) |
| Font loading | `next/font/google`: **Inter** (sans) + **JetBrains Mono** (mono), declared in `src/app/layout.tsx:12-22`, exposed as CSS vars `--font-inter-sans` / `--font-jetbrains-mono` |
| CSS-in-JS | None (no styled-components, emotion, stitches). Some inline `style={{…}}` usage remains. |
| Storybook / visual tests | **None.** No Chromatic, Percy, or Playwright visual snapshots. |
| State / UX libs | `@dnd-kit/*`, `@supabase/ssr`, Zod, `date-fns`. No UI kit (no Radix, no Headless UI, no MUI). |
| Tests | Jest (`jest --coverage`). Contract tests: `src/lib/status.contract.test.ts`, `src/lib/ui-vocab.contract.test.ts`, `tests/ui/no-forbidden-strings.test.ts`. |

---

## 2. Current token inventory

### 2.1 CSS custom properties (`src/app/globals.css`)
- Base: `--background: #f8fafc` (slate-50), `--foreground: #0f172a` (slate-900)
- Spacing: `--space-1..10` → 4/8/12/16/20/24/32/40 px
- Radius: `--radius-sm: 6`, `--radius-md: 8`, `--radius-lg: 12`
- Elevation: `--elevation-1/2/3` (slate-tinted shadows, `rgba(15,23,42,…)`)
- Motion: `--motion-duration-{instant 80, fast 120, base 150, slow

*[truncated — see source for full prompt]*