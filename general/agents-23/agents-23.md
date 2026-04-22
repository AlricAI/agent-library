---
name: AGENTS
description: - This project uses TypeScript with ES modules; prefer named exports and avoid introducing new default exports.
model: claude-sonnet-4-5
---
# Source Code Guidelines

- This project uses TypeScript with ES modules; prefer named exports and avoid introducing new default exports.
- Keep comments focused on current behavior—do not mention deprecated migration phases or future roadmaps.
- Favor small, pure helpers over large multi-purpose functions. If a change affects runtime behavior, add or update tests in the matching `__tests__` folder.
- Use existing path aliases (e.g., `@state/...`, `@persistence/...`) for intra-project imports.