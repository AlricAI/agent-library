# Plan Then Code

> ## Purpose
For complex tasks, create an implementation plan first, get it reviewed, then execute. This prevents the "scope creep PR with 8 merge confl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Plan Then Code

## Purpose
For complex tasks, create an implementation plan first, get it reviewed, then execute. This prevents the "scope creep PR with 8 merge conflicts" problem.

## When to Use
- Tasks touching 3+ files
- Architectural changes (new routes, new database tables, new API endpoints)
- New features (not just bug fixes)
- When previous attempts at the task failed or produced scope-creep PRs
- When the task description is vague and needs interpretation
- Any task where the wrong approach would waste significant time

## When NOT to Use
- Simple one-file bug fixes (use [[agents/skills/visual-bug-fix.md]] instead)
- Research/analysis tasks (no code involved)
- Configuration changes (env vars, settings)

## Pre-Task Context Loading
1. Load company profile and architecture docs from vault
2. Load relevant file contents (read the actual code, don't guess)
3. Load related decision logs from [[decisions/]]
4. Check recent PRs (last 5 merged) for patterns and conventions
5. Load [[agents/skills/codebase-aware.md]] context

## Execution Steps

### Step 1: Understand
- Read ALL relevant code files completely (don't skim)
- Understand the current architecture, patterns, and conventions
- Identify the exact scope of what needs to change
- List any assumptions and validate them against the code
- Note: "I think this file does X" is not good enough -- read it and confirm

### Step 2: Plan
Write a step-by-step implementation plan:
```markdown
## Implementation Plan: [Task Title]

### Files to Modify
1. `path/to/file1.ts` -- [what changes and why]
2. `path/to/file2.ts` -- [what changes and why]

### Files to Create (if any)
1. `path/to/new-file.ts` -- [purpose]

### Steps (in order)
1. [Specific change with code snippet or pseudocode]
2. [Specific change]
3. [Specific change]

### What This Does NOT Change
- [Explicitly list out-of-scope items to prevent scope creep]

### Risks / Edge Cases
- [What could go wrong]
- [What to watch out for]

### Testing
- [How 

*[truncated — see source for full prompt]*