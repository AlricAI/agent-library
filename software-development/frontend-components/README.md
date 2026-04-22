# Frontend Components

> > **Scope:** Frontend
> These coding standards and conventions **must be strictly followed** whenever you work on any frontend UI code, regardless of 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend Components — Agent Instructions

> **Scope:** Frontend
> These coding standards and conventions **must be strictly followed** whenever you work on any frontend UI code, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Core Rule — shadcn/vue Is the Only UI Component Library

**Every UI element in this application must use a shadcn/vue component.** There are no exceptions unless the user explicitly instructs you to create a custom component for a specific, named use case.

- **Never create custom UI components on your own initiative.** If a task appears to require a UI element not yet available as a shadcn/vue component, first check whether it can be composed from existing shadcn/vue components before concluding a custom component is necessary.
- **If and only if** the user explicitly instructs you to create a custom component, place it in `src/custom-components/` — **never** in `src/components/`, which is reserved exclusively for shadcn/vue components installed via the CLI.
- Do not wrap, subclass, or otherwise extend shadcn/vue components into new components without explicit user approval.

---

## 2. Installing shadcn/vue Components

- Add components using the shadcn/vue CLI (`npx shadcn-vue@latest add <component>`). Do not copy component source manually.
- Do not modify the source of installed shadcn/vue components in `src/components/`. They are used **as-is**. If a styling or behaviour change seems necessary, check whether it can be achieved through props, slots, or Tailwind utility classes in the consuming template first.
- If you encounter a situation where the "as-is" constraint causes significant code duplication or complexity, **report it immediately** and start a discussion before modify

*[truncated — see source for full prompt]*