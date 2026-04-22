---
name: Cursor
description: How to load your Context Stack into Cursor IDE.
model: claude-sonnet-4-5
---
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

[Paste relevant sections from your domain-map.md]
```

### Conditional Loading with .mdc Frontmatter

The `.mdc` format supports frontmatter that controls when rules are loaded:

```markdown
---
description: Brand voice for content writing
globs: ["**/*.md", "**/*.mdx", "docs/**"]
alwaysApply: false
---

# Brand Voice

[Paste your brand-voice.md content here]
```

This loads brand-voice only when you are working with markdown or docs files.

**Available frontmatter options:**

| Field | Purpose | Example |
|:------|:--------|:--------|
| `description` | What this rule covers | "Communication style preferences" |
| `alwaysApply` | Load in every session | `true` or `false` |
| `globs` | Load only when working with matching files | `["**/*.ts", "src/**"]` |

### Legacy: .cursorrules File

If you prefer a single-file approach, create `.cursorrules` in your project root:

**File:** `<project-root>/.cursorrules`

```markdown
# Project Context

## Professional Identity
[Paste professional-identity.md content]

## Communication DNA
[Paste communication-dna.md content]

## Domain Map
[Paste domain-map.md and tool-ecosystem.md content]

## Strategic Context
[Paste strategic-context.md content]
```

This is simpler but less flexible than the `.cursor/rules/` approach. You cannot conditionally load sections or organize by concern.


## File Structure at a Glance

```
~/.cursor/
└── rules/
    ├── professional-identity.mdc    # Global: who you are
    ├── communication-dna.mdc        # Global: how you communicate
    └── values-and-boundaries.mdc    # Global: your standards

<project-root>/
├── .cursor/
│   └── rules/
│       ├── strategic-context.mdc    # Project: current priorities
│       ├── domain-map.mdc           # Project: relevant expertise
│       └── tool-ecosystem.mdc       # Project: tech stack
└── .cursorrules                     # Alternative: single-file approach
```


## Mapping Context Components to Cursor Rules

| Component | Where | Loading |
|:----------|:------|:--------|
| professional-identity | Global rules | Always |
| communication-dna | Global rules | Always |
| values-and-boundaries | Global rules | Always |
| decision-architecture | Global rules | Always |
| domain-map | Project rules | Always |
| tool-ecosystem | Project rules | Always |
| strategic-context | Project rules | Always |
| brand-voice | Project rules | Conditional (docs/content files) |
| operating-rhythm | Global rules | Always |
| feedback-journal | Project rules | Always |
| collaboration-profile | Not typically needed in IDE context | Omit |
| learning-edge | Project rules | Conditional or always |


## Token Considerations

Cursor sends rules as part of the context window. More rules mean fewer tokens for conversation.

- Keep each `.mdc` file focused. Separate concerns into individual files rather than one large file.
- Use conditional loading (`globs`) for context that only matters in specific file types.
- If your combined rules exceed 3,000 words, audit for content that could be trimmed or made conditional.


## Testing Your Setup

Open a project with your rules configured and ask Cursor:

```
What do you know about my professional context and preferences?
```

Then test with a code-related task where your context should matter:

```
Review this function and suggest improvements based on my coding standards.
```

If Cursor's suggestions feel generic, check that your `.mdc` files have `alwaysApply: true` (or matching globs) and that the content is specific enough to differentiate your preferences from defaults.