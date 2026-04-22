# Architecture Inventory

> > [!NOTE]  
> **Date:** 2026-02-22  
> This document provides a factual, verified breakdown of the entire architecture without assumptions or future-t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GDVG Admin Console - Architecture Inventory & Audit

> [!NOTE]  
> **Date:** 2026-02-22  
> This document provides a factual, verified breakdown of the entire architecture without assumptions or future-tense generalizations.

### 🏷️ Confidence Tags
| Tag | Description |
|---|---|
| `[VERIFIED]` | Directly observed in code, DB, or logs. |
| `[PARTIAL]` | Observed in code, but full scope or usage is incomplete. |
| `[ASSUMED]` | Inferred logically but not explicitly printed. |
| `[UNKNOWN]` | Not verified or missing. |

---

## 📁 1. REPOSITORY STRUCTURE `[VERIFIED]`

### Top-Level Directories
| Directory | Description |
|---|---|
| `.github/` | Contains Actions workflows for automated CI/CD and cron jobs. |
| `docs/` | Markdown documentation and architectural plans. |
| `public/` | Static assets (images, SVGs). |
| `python/` | Python scripts/packages typically used for custom data extraction and imports. |
| `scripts/` | TypeScript automated scripts (Enrichment, Parsing, Data Quality). |
| `src/` | Next.js frontend code (React components, App Router). |
| `supabase/` | Local Supabase edge functions, migrations, and database configs. |

### Key Workflows (`.github/workflows/`)
| Workflow | Trigger/Schedule | Purpose |
|---|---|---|
| `auto-enrichment-scheduled.yml` | `30 20 * * *` (Daily) | Automated daily enrichment pipeline across sources. |
| `auto-import-manual.yml` | Manual | Trigger for CSV/Kaggle import pipeline. |
| `auto-import-scheduled.yml` | `30 21 * * *` (Daily) | Nightly raw import batch runner. |
| `bulk-import.yml` | Triggers via workflow dispatch | Runs `bulk-import.ts`. |
| `data-quality.yml` | `30 22 * * *` (Daily) | Generates schema integrity reports and checks nulls. |
| `enrich-[entity].yml` | Manual / Dispatch | Discrete enrichment for collections, content, people. |
| `process-imports.yml` | Multiple | Orchestrator for `import_queue` processing. |
| `refresh-queue.yml` | Multiple | Orchestrator for maintaining queue states. |
| `sync-changes

*[truncated — see source for full prompt]*