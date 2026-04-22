# AGENTS

> > **Applies to**: Codex CLI and OpenCode — both read `AGENTS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Routing Guide

> **Applies to**: Codex CLI and OpenCode — both read `AGENTS.md` automatically.  
> For Claude Code, pair this with `CLAUDE.md`. Deeply nested `AGENTS.md` files override parent-level ones.

## Multi-Model Strategy

Use different model tiers for different task complexities.
Prefer tier labels in shared guidance and keep exact model names in local config.

**OpenCode with oh-my-openagent** ([reference config](../implementations/opencode/oh-my-openagent.jsonc)):

Sisyphus delegates by **category**, not model name. Keep the routing categories
stable and let the live config own the exact provider/model mapping.

| Agent | Tier | Use For |
|-------|------|---------|
| **Sisyphus** | Deep reasoning | Default orchestrator — plans, delegates, drives to completion |
| **Hephaestus** | Deep reasoning | Deep architecture, multi-file debugging, cross-domain reasoning |
| **Prometheus** | Deep reasoning | Strategic planning and interview mode |
| **Oracle** | Deep reasoning | Architecture consultation, trade-off analysis |
| **Librarian** | Deep reasoning | Documentation search, code reference, pattern lookup |
| **Atlas** | Balanced | Todo orchestration and parallel execution |
| **Sisyphus-Junior** | Balanced | Sub-tasks delegated from Sisyphus |
| **Explore** | Fast | Fast codebase grep, quick lookups |

| Category | Tier | Trigger |
|----------|------|---------|
| `visual-engineering` | Visual specialist | UI/UX, CSS, design, animation |
| `ultrabrain` | Deep reasoning | Deep architecture, complex reasoning |
| `deep` | Deep reasoning | Autonomous research, thorough investigation |
| `artistry` | Visual or creative specialist | Creative or unconventional approaches |
| `writing` | Balanced | Docs, CHANGELOG, README, prose |
| `quick` | Fast | Trivial edits, typo fixes, single-line changes |
| `unspecified-low` | Balanced | General low-effort tasks |
| `unspecified-high` | Balanced or deep reasoning | General high-effort tasks |

**Vanilla OpenCode agent

*[truncated — see source for full prompt]*