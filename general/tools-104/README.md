# TOOLS

> Diff parsing, branch management, gh CLI patterns.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — Auto-PR Writer

Diff parsing, branch management, gh CLI patterns.

---

## Diff Parsing

Issue body has a `## Proposed fix` section. Inside it, look for blocks like:

```markdown
File: `path/to/file.ts:LINE`
Old:
\`\`\`<lang>
<exact existing content>
\`\`\`
New:
\`\`\`<lang>
<exact replacement>
\`\`\`
```

Or sometimes just:

```markdown
File: `path/to/file.ts`
Old:
\`\`\`
<existing>
\`\`\`
New:
\`\`\`
<replacement>
\`\`\`
```

Parser:
1. Split section into "## Proposed fix" through next "##" header
2. Match each `File:` line as the start of an edit block
3. Capture lang-tagged code blocks as Old/New
4. Resulting list: `[{filepath, old, new}, ...]`

If parsing produces 0 edits, the issue is malformed — skip and report.

---

## Path Allowlist (Strict)

These paths are SAFE to edit:
- `forge-orchestrator/src/**/*.ts`
- `dashboard/src/**/*.tsx`
- `dashboard/src/**/*.ts`
- `companies/*/agents/*/*.md`
- `vault/agents/skills/*.md`
- Test files under `*/__tests__/**`

These paths are FORBIDDEN:
- `supabase/migrations/**`
- `.env*`
- `**/credentials*`
- `**/secrets*`
- `package.json` (lockfiles only via npm install, not direct edit)
- `tsconfig.json`
- `next.config.js`
- `forge-orchestrator/.env*`

If ANY file in the proposed diff matches a forbidden path, skip the issue.

---

## Branch Hygiene

```bash
# Always start from clean main
cd /Users/dirtsyncmini/MCMForge
git fetch origin
git checkout main
git reset --hard origin/main  # discard any leftover state

# Create branch
git checkout -b agent/auto-pr-<id-lowercase>

# After failure
git checkout main
git branch -D agent/auto-pr-<id-lowercase>
```

If a branch with the same name already exists from a prior failed attempt, delete it before recreating.

---

## Test Commands

```bash
# Dashboard typecheck
cd /Users/dirtsyncmini/MCMForge/dashboard && npx tsc --noEmit

# Orchestrator typecheck
cd /Users/dirtsyncmini/MCMForge/forge-orchestrator && npx tsc --noEmit

# Vitest (one file)
cd /Users/dirtsyncmini/MCMFo

*[truncated — see source for full prompt]*