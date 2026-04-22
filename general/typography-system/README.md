# TYPOGRAPHY SYSTEM

> **Source of truth:** `design-system/README.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Typography System

**Source of truth:** `design-system/README.md` + `design-system/colors_and_type.css`.
All brand tokens (colours, type scale, font stacks, radii, shadows, motion) live there. Do not edit them here.

This file only records the **app's intentional deviations** from the brand spec, so future agents don't "correct" them back to the DS defaults.

## Canonical tokens (where to look)

- Primary sans: **Lexend** (weights 300/400/500/600/700), loaded via `next/font/google` in `src/app/layout.tsx`, exposed as CSS var `--font-lexend-sans`, and mapped to Tailwind `font-sans` via `@theme inline` in `src/app/globals.css`.
- Mono: **JetBrains Mono**, exposed as `--font-jetbrains-mono`, mapped to Tailwind `font-mono`.
- Colour tokens: `--color-ink` (body / headings), `--color-navy-500` (meta / secondary), `--color-navy-500/60` (disabled), `--color-brand` (Blurple links) — defined in `globals.css`, sourced from `--sh-*` brand ramps.
- Typography constants: `src/lib/typography.ts` (`TYPOGRAPHY.*` keys) consume the tokens above.
- Typography utility classes: `.page-title`, `.section-title`, `.subsection-label`, `.table-header-text`, `.body-text`, `.meta-text`, `.disabled-text`, `.text-secondary`, `.monospace-technical`, `.tabular-nums` in `globals.css`.

## App deviations from the design-system spec

These are intentional and should not be reverted to the DS defaults without an explicit product decision. They are recorded in `design-system/MIGRATION_AUDIT.md` §§11.2–11.4.

1. **Body size: 14px** (DS spec: 16px).
   The DS 16px applies to marketing / docs surfaces. App density wins here — lifting to 16px re-paginates every table, list, and form. Marketing exceptions: `/login` and `/` render at the DS 16px.
2. **Body weight: 400** (DS spec: 300 Light).
   Light 300 at 14px is a legibility gamble on non-retina displays. Use 300 only for large display type (H1 / H2 at 32 px+).
3. **Split button radii** (DS spec: 20px everywhere).
   - `--radius-button-cta: 20px` for ma

*[truncated — see source for full prompt]*