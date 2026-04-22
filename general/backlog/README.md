# BACKLOG

> **Repository:** `midnghtsapphire/reese-reviews`
**Last Updated:** April 5, 2026
**Standard:** revvel-standards/MASTER_APP_TEMPLATE.md

---

## How to 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Product Backlog — Reese Reviews

**Repository:** `midnghtsapphire/reese-reviews`
**Last Updated:** April 5, 2026
**Standard:** revvel-standards/MASTER_APP_TEMPLATE.md

---

## How to Use This Backlog

This is the **single source of truth** for all outstanding work on Reese Reviews — for both human contributors and AI agents.

### For Humans (Audrey / Team Members)
1. Add new items in the **📥 Inbox** section at the bottom.
2. Move items to the correct priority tier after review.
3. Assign an owner and update the status column when work starts.
4. Mark items `Done` and log the completion date.

### For AI Agents
1. **Read this file before writing any code.**
2. Pick the **highest-priority `To Do`** item in the current sprint tier.
3. Update the item status to `In Progress` with your session date.
4. Complete the task. Run tests. Push your changes.
5. Update the item to `Done` with the PR/commit reference.
6. Update `docs/scrum/HANDOFF.md` before ending your session.
7. **Do not start a new item until the current one is verified complete.**

> ⚠️ **Rule:** One item per agent session. Finish it completely before moving on.  
> ⚠️ **Rule:** If a task is too large to finish in one session, break it into sub-tasks here first.

---

## Status Key

| Status | Meaning |
| :--- | :--- |
| `To Do` | Not started. Ready to be picked up. |
| `In Progress` | Actively being worked on. Include agent/date. |
| `Blocked` | Cannot proceed — dependency or question needed. |
| `In Review` | PR open, awaiting merge. |
| `Done` | Merged, verified. |
| `Deferred` | Intentionally pushed to a later sprint. |

---

## Sprint 4 — Security & Integrations (Current Sprint)

**Sprint Goal:** Address critical security gaps, complete Plaid/Stripe backend wiring, and fix top ESLint violations.

| ID | Priority | Title | Owner | Status | Acceptance Criteria | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| RR-401 | 🔴 Critical | Migrate Admin Panel API keys from localStorage to env vars 

*[truncated — see source for full prompt]*