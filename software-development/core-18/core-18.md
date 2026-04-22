---
name: Core
description: **Goal:** Analyze screenshot, find the broken code, make the minimal fix, create PR.
model: claude-sonnet-4-5
---
# Skill: visual-bug-fix

**Goal:** Analyze screenshot, find the broken code, make the minimal fix, create PR.

**Model:** Claude (required — needs vision capability). Gemini fallback. Never Codex.

**Constraint:** Fix ONLY what's in the screenshot. No refactoring. No scope creep.

**Trigger:** screenshot of UI bug, CSS issue, layout broken, visual regression, Telegram screenshot