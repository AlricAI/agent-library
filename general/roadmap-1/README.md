# ROADMAP

> **Last Updated:** 2026-04-20 (v16 audit — 1:46am ET)
**Status:** M1–M4 ✅ | M5 In Progress (beta launch) | 8/8 PASS ✅ | B2B 67.0% 🆕
**Repo:** [anchapi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PortKit — Development Roadmap

**Last Updated:** 2026-04-20 (v16 audit — 1:46am ET)
**Status:** M1–M4 ✅ | M5 In Progress (beta launch) | 8/8 PASS ✅ | B2B 67.0% 🆕
**Repo:** [anchapin/ModPorter-AI](https://github.com/anchapin/ModPorter-AI) | Rebranded to PortKit ✅ (#1114)
**Target:** Public launch at modporter.ai by June 22, 2026

---

## Executive Summary

PortKit converts Minecraft Java mods to Bedrock add-ons. Positioned as a **B2B conversion accelerator** targeting Marketplace creators.

**B2B readiness: 67.0%** (v16, 8/8 PASS). M1–M4 all complete. The 4-cycle ceiling at 66.4% was broken in v16 by #1119 (Create custom recipe converters): Create recipes 36% → 40%, aggregate recipes 41.7% → 45.0%. ~126 of 750 Create custom recipes now convert (~21% of custom types). Remaining Create recipe coverage (1,661 unconverted) is the top remaining lever for B2B growth.

**Pipeline state**: tree-sitter (Java 17+) ✅ | minecraft-data 1152 items ✅ | confidence scoring ✅ | semantic chunking ✅ | java_analyzer 6-module package ✅ | Celery task queues ✅ | texture/model converter subpackages ✅ | Create recipe converters (milling/crushing/deploying/splashing/compacting) ✅ | DPC multi-candidate consistency selection ✅

---

## Conversion Audit History

| Cycle | Date | Mods | Textures | Models | Recipes | Sound | Lang | B2B est. | Key Changes |
|-------|------|------|----------|--------|---------|-------|------|-----------|-------------|
| v1 | Apr 8 | 8 | ~0% | 0% | 0% | 0% | 0% | ~5% | Baseline |
| v2 | Apr 9 | 8 | 54.8% | 0.2% | 0% | 0% | 0% | ~25% | Bulk texture extraction |
| v5 | Apr 11 | 8 | 54.7% | 82.3% | 25.8% | 0% | 0% | ~46% | Model+recipe converters wired |
| v6 | Apr 15 | 30 | 68.7% | 68.3% | 40.2% | 0% | 0% | ~49% | NeoForge fix, 30-mod set |
| v7 | Apr 16 | 8 | 54.7% | 82.3% | 25.8% | ~100% | 89.3% | ~63% 🎯 | Sound+lang, loot tables, spawn rules |
| v9 | Apr 18 00:06 | 8 | 54.7% | 82.3% | 26.6% | ~100% | 89.3% | 63.4% | Cooking recipe fix +27 |
| v10 | Apr 18 10:15 |

*[truncated — see source for full prompt]*