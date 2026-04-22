# Context Building

> > The single most impactful thing you can do for AI-assisted development is give the agent the right context before it writes a single line of code.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Context Building

> The single most impactful thing you can do for AI-assisted development is give the agent the right context before it writes a single line of code.

## The Problem

AI agents are only as good as the context they receive. A powerful model with zero project context produces generic code. A mediocre model with excellent context produces code that fits your project perfectly.

## The Pattern

Every project should have a **context layer** — a set of files that any AI agent reads before doing work. The filenames vary by tool, but the content pattern is universal.

### Context File Mapping

| Tool | Primary File | Secondary File |
|------|-------------|----------------|
| Claude Code | `CLAUDE.md` | — |
| OpenCode | `AGENTS.md` | `CLAUDE.md` |
| Cursor | `.cursorrules` | `.cursor/rules/*.mdc` |
| GitHub Copilot | `COPILOT.md` | `.github/copilot-instructions.md` |
| Windsurf | `.windsurfrules` | — |
| Any tool | `CONVENTIONS.md` | — |

### What to Include

**Always include (high signal):**

```markdown
# Project Name

## Quick Reference
- Build: `npm run build`
- Test: `npm test`
- Lint: `npm run lint`
- Dev: `npm run dev`

## Architecture
- Brief description of project structure
- Key directories and their purpose
- Tech stack (framework, database, deployment)

## Code Standards
- Language conventions (functional vs OOP, naming)
- Line length, function size limits
- Import ordering, file organization

## Workflow
- Branch naming convention
- Commit message format
- PR process
```

**Never include (noise):**
- Full API documentation (agent can read the code)
- Dependency lists (agent reads package.json)
- Historical changelog (agent reads git log)
- Tutorial-style explanations

### The 80/20 Rule

80% of context value comes from:
1. **How to run things** — build, test, lint commands
2. **Where things are** — project structure, key directories
3. **What not to do** — gotchas, anti-patterns, past mistakes

## Progressive Context

Don't dump everything in 

*[truncated — see source for full prompt]*