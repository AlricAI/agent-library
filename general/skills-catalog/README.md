# SKILLS CATALOG

> > **Auto-generated Documentation** — Last updated: 2026-04-14 23:14
>
> This catalog is automatically maintained. Update it by running:
> ```bash
> py

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skills Catalog

> **Auto-generated Documentation** — Last updated: 2026-04-14 23:14
>
> This catalog is automatically maintained. Update it by running:
> ```bash
> python skill-creator/scripts/update_catalog.py --skills-dir skills/
> ```

This document provides comprehensive documentation on available skills, how to use them, and when each skill should be triggered.

---

## Table of Contents

- [What Are Skills?](#what-are-skills)
- [Available Skills](#available-skills)
  - [Claude Code Design](#claude-code-design)
  - [Cowork Export](#cowork-export)
  - [Documentation](#documentation)
  - [Image Ai Generator](#image-ai-generator)
  - [Notebooklm](#notebooklm)
  - [Notebooklm Internal](#notebooklm-internal)
  - [Pdf Reader](#pdf-reader)
  - [Plugin Discovery](#plugin-discovery)
  - [Qdrant Memory](#qdrant-memory)
  - [Resend](#resend)
  - [Supply Chain Monitor](#supply-chain-monitor)
  - [Upstream Sync](#upstream-sync)
  - [Webcrawler](#webcrawler)
- [Using Skills](#using-skills)
- [Creating New Skills](#creating-new-skills)
- [Maintenance](#maintenance)

---

## What Are Skills?

**Skills** are modular, self-contained packages that extend the AI agent's capabilities with specialized knowledge, workflows, and tools.

### Skill Structure

```
skill-name/
├── SKILL.md           # (required) Main instruction file
├── scripts/           # (optional) Executable scripts
├── references/        # (optional) Documentation
└── assets/            # (optional) Templates, images, etc.
```

---

## Available Skills

### Claude Code Design

| Property | Value |
| -------- | ----- |
| **Name** | `claude-code-design` |
| **Location** | `skills/claude-code-design/` |
| **Type** | Standalone |

**Description:** "Answer questions about Claude Code / Anthropic agent design patterns (CLAUDE.md layering, skills anatomy, progressive disclosure, memory-first, orchestration, sub-agents, worktree isolation, Karpathy loop). Primary backend is a NotebookLM RAG over Anthropic design notebooks

*[truncated — see source for full prompt]*