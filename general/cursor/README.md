# Cursor

> How to load your Context Stack into Cursor IDE.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cursor

How to load your Context Stack into Cursor IDE.

Cursor reads context from rules files at both global and project levels. It also supports `.mdc` files with frontmatter that controls when specific rules are loaded.


## Context Loading Mechanisms

Cursor has three context layers:

1. **Global rules** (`~/.cursor/rules/`): Apply to every project
2. **Project rules** (`.cursor/rules/` in project root): Apply to the current project
3. **Legacy project rules** (`.cursorrules` in project root): Single file, project-level

All accept plain markdown. The `.cursor/rules/` directory approach is preferred because it supports multiple files and conditional loading.


## Recommended Setup

### Global Rules: Self and Style

Create files in your global rules directory for context that applies everywhere.

**Directory:** `~/.cursor/rules/`

```
~/.cursor/rules/
├── professional-identity.mdc
├── communication-dna.mdc
└── values-and-boundaries.mdc
```

**Example: `~/.cursor/rules/professional-identity.mdc`**

```markdown
---
description: Professional identity and context for all interactions
alwaysApply: true
---

# Professional Identity

[Paste your professional-identity.md content here]
```

**Example: `~/.cursor/rules/communication-dna.mdc`**

```markdown
---
description: Communication style preferences
alwaysApply: true
---

# Communication DNA

[Paste your communication-dna.md content here]
```

The `alwaysApply: true` frontmatter ensures these load in every session. Other frontmatter options allow conditional loading.

### Project Rules: Substance and Situation

Create project-specific rules in each project's `.cursor/rules/` directory.

**Directory:** `<project-root>/.cursor/rules/`

```
<project-root>/.cursor/rules/
├── strategic-context.mdc
├── domain-map.mdc
└── tool-ecosystem.mdc
```

**Example: `<project-root>/.cursor/rules/domain-map.mdc`**

```markdown
---
description: Domain expertise and knowledge areas for this project
alwaysApply: true
---

# Domain Map



*[truncated — see source for full prompt]*