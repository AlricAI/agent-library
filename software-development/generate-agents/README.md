# Generate Agents

> Analyze codebase and generate hierarchical AGENTS.md structure

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Task: Analyze this codebase and generate a hierarchical AGENTS.md structure

## Context & Principles

You are going to help me create a **hierarchical AGENTS.md system** for this codebase. This is critical for AI coding agents to work efficiently with minimal token usage.

### Core Principles:
1. **Root AGENTS.md is LIGHTWEIGHT** - Only universal guidance, links to sub-files
2. **Nearest-wins hierarchy** - Agents read the closest AGENTS.md to the file being edited
3. **JIT (Just-In-Time) indexing** - Provide paths/globs/commands, NOT full content
4. **Token efficiency** - Small, actionable guidance over encyclopedic documentation
5. **Sub-folder AGENTS.md files have MORE detail** - Specific patterns, examples, commands

## Your Process

### Phase 1: Repository Analysis
First, analyze the codebase structure and provide me with:

1. **Repository type**: Monorepo, multi-package, or simple single project?
2. **Primary technology stack**: Languages, frameworks, key tools
3. **Major directories/packages** that should have their own AGENTS.md:
   - Apps (e.g., `apps/web`, `apps/api`, `apps/mobile`)
   - Services (e.g., `services/auth`, `services/transcribe`)
   - Packages/libs (e.g., `packages/ui`, `packages/shared`)
   - Workers/jobs (e.g., `workers/queue`, `workers/cron`)
   
4. **Build system**: pnpm/npm/yarn workspaces? Turborepo? Lerna? Or simple?
5. **Testing setup**: Jest, Vitest, Playwright, pytest? Where are tests?
6. **Key patterns to document**:
   - Code organization patterns
   - Important conventions (naming, styling, commits)
   - Critical files that serve as good examples
   - Anti-patterns to avoid

Present this as a **structured map** before generating any AGENTS.md files.

---

### Phase 2: Generate Root AGENTS.md

Create a **lightweight root AGENTS.md** (~100-200 lines max) that includes:

#### Required Sections:

**1. Project Snapshot** (3-5 lines)
- Repo type (monorepo/simple)
- Primary tech stack
- Note that sub-packages have their own AGENTS.md fi

*[truncated — see source for full prompt]*