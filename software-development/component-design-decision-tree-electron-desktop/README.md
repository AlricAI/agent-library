# Component Design Decision Tree (Electron Desktop)

> description: Component design decision tree for Electron desktop UI components globs: - "packages/**/components/**/*"

## Tags
`typescript` `react`

## System Prompt
---
description: Component design decision tree for Electron desktop UI components
globs:
  - "packages/**/components/**/*"
  - "packages/**/ui/**/*"
  - "apps/*/src/components/**/*"
scopes:
  - react
  - frontend
  - ui
  - components
  - architecture
  - electron
alwaysApply: false
---

# Component Design Decision Tree (Electron Desktop)

## 🎯 Purpose
This rule provides a clear decision-making framework for choosing component patterns in the **Electron desktop renderer**. Since this is a desktop-only application, mobile/responsive patterns are not applicable.

---

## 📊 Decision Flow

### Step 1: Is this a third-party component wrapper?

**YES** → Create wrapper component
- Wrap Mantine or other library components with project-specific defaults
- Place in appropriate directory (`src/ui/` or `components/`)
- Create Storybook stories to document variants
- Example: Custom Button wrapping `@mantine/core` Button with PM Agent theme

**NO** → Continue to Step 2

---

### Step 2: Is this a new reusable component (not a page)?

**YES** → Follow **Storybook-First Development**
- Build component in isolation first
- Create `.stories.tsx` with all variants and states
- Test component independently before integration
- Document props and usage patterns

**NO** → Continue to Step 3

---

### Step 3: Is this a complex feature component?

**YES** → Use **Bulletproof Pattern**
- Follow `react-bulletproof-component-pattern.rules.mdc`
- Separate concerns: component, styles, types, tests
- Use co-location for related files
- Ensure proper error boundaries

**NO** → Simple component, use basic React patterns

---

## 🔄 Common Patterns for PM Agent

### Pattern 1: Wrapped UI Library Component (Storybook)
**Use for:** Buttons, Inputs, Cards from Mantine
```
src/ui/Button/
├── Button.tsx         # Wrapper with PM Agent defaults
├── Button.stories.tsx # All variants
└── Button.test.tsx    # Component tests
```

### Pattern 2: Custom Reusable Component (Bulletproof + Storybook)
**Use 

*[truncated — see source for full prompt]*