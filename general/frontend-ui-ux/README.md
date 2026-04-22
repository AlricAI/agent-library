# Frontend Ui Ux

> > **Scope:** Frontend
> These UI/UX standards **must be strictly followed** whenever you create, modify, or review any frontend design or interface co

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend UI/UX Design — Agent Instructions

> **Scope:** Frontend
> These UI/UX standards **must be strictly followed** whenever you create, modify, or review any frontend design or interface code, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Consistency & Simplicity

- Use the same colors, fonts, spacing scale, and icon set throughout the entire application. Never introduce one-off values; rely on the Tailwind CSS theme tokens already configured in the project.
- Keep all user-facing text short and direct: labels, button copy, empty-state messages, and error strings must all be concise and meaningful.
- Every page must contain only the interface elements required for its primary task. Remove any decorative or secondary element that does not directly help the user complete that task.
- Prefer familiar, conventional UI patterns (e.g., a top navigation bar, a standard form layout) over novel ones. Surprise the user as little as possible.

---

## 2. Accessibility (a11y)

- Use semantic HTML elements (`<nav>`, `<main>`, `<section>`, `<article>`, `<header>`, `<footer>`, `<button>`, `<a>`, etc.) wherever appropriate. Never use a `<div>` or `<span>` as an interactive element.
- Every interactive element must be reachable and operable via keyboard alone (Tab, Shift+Tab, Enter, Space, Escape, arrow keys where applicable).
- Provide descriptive `aria-label` or `aria-labelledby` attributes on controls whose visible label is insufficient or absent (e.g., icon-only buttons).
- Maintain a minimum contrast ratio of **4.5 : 1** for normal text and **3 : 1** for large text, following WCAG 2.1 AA guidelines.
- All images and icons that convey meaning must have an `alt` attribute (or `aria-hidden="true"` when purely de

*[truncated — see source for full prompt]*