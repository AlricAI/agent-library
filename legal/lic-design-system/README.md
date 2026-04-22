# lic-design-system

> Enforce the LIC brand identity, visual tokens, UI kit constraints, interaction doctrine, AI interaction model, and GP-01 workflow standards in web apps. Use when asked to apply this design system to an existing repo, build new screens/components that must match LIC standards, or review UI work for compliance.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LIC Design System

Use this skill to implement or enforce the LIC standards manual in product UI, marketing pages, AI interface surfaces, and GP-01 intake-to-matter workflows.

## Reference Loading Map

Read only the files needed for the current task.

- Always load first:
  - `references/design-tokens.md`
  - `references/brand-foundation.md`
- Load for app UI/components:
  - `references/ui-kit.md`
- Load for interaction behavior or AI UX:
  - `references/interaction-and-ai.md`
- Load for marketing site work:
  - `references/marketing-site.md`
- Load for intake-to-matter flow/screen work:
  - `references/gp01-flow.md`
- Load for reusable user prompts in a new repo:
  - `references/adoption-prompt.md`

## Implementation Workflow

1. Determine target surface.
- Classify task as `product-app`, `marketing-site`, `ai-interface`, `gp01-flow`, or mixed.
- Choose references from the map above.

2. Audit the target repo before editing.
- Identify stack (React/Next/Vue, Tailwind/CSS Modules, component library).
- Locate global style entrypoints and design token sources.
- Locate base components (button, input, modal, table, badge, nav).

3. Apply the token and typography layer.
- Install LIC color, type, spacing, radius, and border tokens from `references/design-tokens.md`.
- Preserve semantic token aliases so product code can consume consistent names.

4. Retrofit primitives and shared components.
- Normalize components to LIC constraints from `references/ui-kit.md`.
- Prioritize: button, input, select, textarea, badge, card, table, dialog/modal, alert/toast, tabs, pagination.

5. Enforce interaction and AI behavior rules.
- Apply focus, feedback, loading, modal, validation, and accessibility rules from `references/interaction-and-ai.md`.
- For AI surfaces, apply command-surface and provenance rules from `references/interaction-and-ai.md`.

6. Apply context-specific standards.
- For public pages, apply `references/marketing-site.md`.
- For intake-to-matter workflows, apply

*[truncated — see source for full prompt]*