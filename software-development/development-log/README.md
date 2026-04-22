# DEVELOPMENT LOG

> Full log of product development from inception to present.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Development Log — Findash / Octopus Trading Platform

Full log of product development from inception to present. Use the parameters below when adding new entries so the log stays consistent.

---

## Log entry parameters

Each entry should include these fields where applicable:

| Parameter   | Required | Description |
|------------|----------|-------------|
| **date**   | Yes      | Date of the change (YYYY-MM-DD). |
| **version**| No       | Release or app version if applicable (e.g. `3.3.0`, `0.4.0`). |
| **area**   | Yes      | Area of the product: `backend` \| `frontend` \| `infra` \| `docs` \| `ops` \| `fullstack` \| `project`. |
| **type**   | Yes      | Kind of change: `added` \| `changed` \| `fixed` \| `removed` \| `breaking` \| `refactor`. |
| **summary**| Yes      | One-line description of what was done. |
| **details**| No       | Bullet points or short paragraph for context. |
| **ref**    | No       | Issue/PR/ticket (e.g. `#8`, `GH-10`). |

**Example:**

```markdown
| 2026-02-19 | 0.4.0 | frontend | changed | Sidebars expand on hover, collapse on mouse leave. | Left/right desktop nav; 200ms leave delay. | |
```

---

## How to update this log

1. **When shipping a feature or fix:** Add a new row to the table in the next section (or a new “Recent” subsection) with the parameters above.
2. **When cutting a release:** Add a `## [Version] - YYYY-MM-DD` section; move recent table rows into it or summarize under Added/Changed/Fixed.
3. **Keep the schema:** Use the same column order and types so the log stays machine- and human-readable.

---

## Full development timeline

### [1.0.0] — 2025-06-01 · Initial release

| Date       | Version | Area     | Type    | Summary | Details | Ref |
|------------|---------|----------|---------|---------|---------|-----|
| 2025-06-01 | 1.0.0   | project  | added   | Initial release. | Basic project structure, core trading functionality. | |

---

### [2.0.0] — 2025-08-01 · Trading platform

| Date       | Version | Area

*[truncated — see source for full prompt]*