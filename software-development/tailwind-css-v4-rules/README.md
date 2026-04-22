# Tailwind CSS v4 Rules

> globs: "**/*.{css,scss,vue,tsx,jsx}" Tailwind CSS v4 Rules ## Core Changes from v3

## Tags
`vue` `tailwind`

## System Prompt
---
globs: "**/*.{css,scss,vue,tsx,jsx}"
---

# Tailwind CSS v4 Rules

### Core Changes from v3
- **CSS-first config** — no `tailwind.config.js` by default
- **Single import** — `@import "tailwindcss"` replaces `@tailwind base/components/utilities`
- **Auto content detection** — no `content` array needed
- **Built-in Lightning CSS** — no `autoprefixer` or `postcss-import` needed
- **5x faster builds**, 100x+ faster incremental

### Setup

**Vite**: `import tailwindcss from "@tailwindcss/vite"; export default { plugins: [tailwindcss()] }`

**PostCSS**: `export default { plugins: { "@tailwindcss/postcss": {} } }`

**CSS**: `@import "tailwindcss"`

### \@theme Directive

All customization in CSS via `@theme`. Variables auto-generate utilities:

```css
@theme {
  --color-brand: #3b82f6;        /* → bg-brand, text-brand */
  --font-display: "Inter";       /* → font-display */
  --spacing-18: 4.5rem;          /* → p-18, m-18, gap-18 */
  --breakpoint-3xl: 1920px;      /* → 3xl:flex */
  --radius-pill: 9999px;         /* → rounded-pill */
  --animate-fade-in: fade-in 0.3s ease-out;
  @keyframes fade-in { from { opacity: 0; } to { opacity: 1; } }
}
```

**Override defaults**: `--color-*: initial;`. **Reference vars**: `@theme inline` (no :root variable)

### Directives Quick Reference

| Directive | Purpose |
|-----------|---------|
| `@import "tailwindcss"` | Load Tailwind |
| `@theme { }` | Define theme variables |
| `@config "./file.js"` | Load JS config (migration) |
| `@source "../path"` / `not` | Add/exclude content paths |
| `@plugin "@tailwindcss/forms"` | Load plugins |
| `@utility name { }` | Custom utility with variants |
| `@variant dark { }` | Apply variant in CSS |
| `@custom-variant name (selector)` | Define custom variant |
| `@reference "../app.css"` | Reference in scoped styles |

### Custom Utilities

**MUST use `@utility` for variant support** (not `@layer utilities`):
```css
@utility content-auto { content-visibility: auto; }  /* Works with hover:, dark

*[truncated — see source for full prompt]*