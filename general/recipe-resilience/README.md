# RECIPE RESILIENCE

> This document describes two resilience improvements to the amplihack recipe runner:

1. **Branch Name Sanitization** (Issue #2952) — `default-workflow

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Recipe Resilience: Branch Sanitization & Sub-Recipe Recovery

This document describes two resilience improvements to the amplihack recipe runner:

1. **Branch Name Sanitization** (Issue #2952) — `default-workflow` step 4 now
   produces valid git branch names from any `task_description`, including
   multi-line prompts and strings with special characters.
2. **Sub-Recipe Agentic Recovery** (Issue #2953) — when a sub-recipe step fails,
   the runner invokes an agent recovery step before raising a hard error, giving
   the workflow a chance to self-heal.

---

## Branch Name Sanitization

### Problem

`step-04-setup-worktree` in `amplifier-bundle/recipes/default-workflow.yaml`
creates a git worktree using a branch name derived from `task_description`.
Before this fix, the raw value was used directly. Multi-line task descriptions
(common when pasting from issue bodies or commit messages) produced branch names
containing newlines, which git rejects immediately:

```
fatal: 'fix login bug\nwith oauth' is not a valid branch name
```

Other common failure modes:

| Input character     | Git error                                         |
| ------------------- | ------------------------------------------------- |
| Uppercase letters   | Branch created but inconsistent with tooling      |
| `(`, `)`, `/`, `:`  | Branch name parsing failures in some git versions |
| Names > 60 chars    | Unwieldy; can hit filesystem path-length limits   |
| Trailing `.` or `-` | `git check-ref-format` rejects them               |

### Solution: Sanitization Pipeline

Step 4 now runs `task_description` through a shell pipeline before constructing
the branch name:

```
newlines → spaces
→ strip leading/trailing whitespace
→ lowercase
→ replace invalid chars ([^a-z0-9_.-]) with hyphens
→ collapse consecutive hyphens
→ truncate to 60 characters
→ strip trailing hyphens and dots
→ validate with git check-ref-format --branch
→ fallback to {prefix}/issue-{n}-task if invalid
```

The resulting slug

*[truncated — see source for full prompt]*