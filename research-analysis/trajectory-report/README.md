# Trajectory Report

> Deep analysis of agent behavior across 18 inference runs on `BurntSushi__ripgrep-2626`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Trajectory Analysis Report

Deep analysis of agent behavior across 18 inference runs on `BurntSushi__ripgrep-2626`.

**Runs analyzed:** 18
**Runs with tool actions:** 18
**Runs with message-format events:** 2

---

## 1. Tool Usage Patterns

| Run | T | Actions | Views | Edits | Terminal | Think | Strategy |
|-----|---|---------|-------|-------|----------|-------|----------|
| single-instance | 0.2 | 11 | 0 | 0 | 0 | 0 | message-format (no tool actions parsed) |
| t00-s1 | 0.0 | 29 | 6 | 0 | 22 | 1 | investigate-only: explore → reproduce → git-history |
| t00-s2 | 0.0 | 29 | 6 | 0 | 21 | 2 | reproduce-only: explore → attempt reproduction |
| t02-s1 | 0.2 | 30 | 6 | 0 | 22 | 2 | reproduce-only: explore → attempt reproduction |
| t02-s2 | 0.2 | 29 | 5 | 0 | 23 | 1 | reproduce-only: explore → attempt reproduction |
| t02-s3 | 0.2 | 29 | 10 | 4 | 14 | 1 | full-cycle: explore → edit → test → build |
| t02-s4 | 0.2 | 30 | 12 | 1 | 17 | 0 | full-cycle: explore → edit → test → build |
| t02-s5 | 0.2 | 29 | 8 | 2 | 18 | 1 | full-cycle: explore → edit → test → build |
| t05-s1 | 0.5 | 11 | 0 | 0 | 0 | 0 | message-format (no tool actions parsed) |
| t05-s2 | 0.5 | 29 | 7 | 0 | 21 | 1 | investigate-only: explore → reproduce → git-history |
| t05-s3 | 0.5 | 30 | 8 | 4 | 18 | 0 | full-cycle: explore → edit → test → build |
| t05-s4 | 0.5 | 30 | 10 | 3 | 17 | 0 | full-cycle: explore → edit → test → build |
| t05-s5 | 0.5 | 29 | 6 | 0 | 22 | 1 | reproduce-only: explore → attempt reproduction |
| t08-s1 | 0.8 | 29 | 8 | 0 | 20 | 1 | investigate-only: explore → reproduce → git-history |
| t08-s2 | 0.8 | 29 | 6 | 0 | 22 | 1 | investigate-only: explore → reproduce → git-history |
| t08-s3 | 0.8 | 11 | 7 | 1 | 3 | 0 | edit-and-verify: explore → edit → test |
| t08-s4 | 0.8 | 29 | 11 | 3 | 15 | 0 | full-cycle: explore → edit → test → build |
| t08-s5 | 0.8 | 30 | 9 | 2 | 19 | 0 | full-cycle: explore → edit → test → build |

### Tool Distribution (across all runs)

- **file_editor

*[truncated — see source for full prompt]*