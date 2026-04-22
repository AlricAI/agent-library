# DEVELOPMENT PLAN V2.0

> > Plan date: 2026-04-17
> Reviewed by: Codex (2026-04-17, 3 critical issues found and addressed in v2 of this doc)
> Status: READY FOR EXECUTION

---


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Pulse v2.0 — Cost-to-Code Yield Score

> Plan date: 2026-04-17
> Reviewed by: Codex (2026-04-17, 3 critical issues found and addressed in v2 of this doc)
> Status: READY FOR EXECUTION

---

## 一、Why this feature

### Strategic context (from PORTFOLIO_REVIEW_2026-04-16.md)

CLI Pulse 在 portfolio 里被标为 **#1 priority**（developer-paying market, $5-20K MRR ceiling — 比 Kinen 的 $500-1.5K 高 10x）。Cost-to-Code Yield Score 被标为 **the killer feature** —— 因为它回答了用户已在问但没工具能答的问题：

> "Cursor $20/mo 值不值？它给我产了多少代码？"
> "Claude Pro vs Codex Pro，哪个对我 ROI 更高？"
> "我这个月花在 AI 上的钱，换成了多少 commits？"

### Why competitors don't have this

- **Helicone / Vantage**：只追踪 token usage，不连接 git。
- **Cursor / Codex / Claude 自己**：只露自己单个产品的数据。
- **CLI Pulse 的独特位置**：唯一一个**跨 provider 聚合 + 本地（能访问 git）**的工具。这是结构性优势。

### Success metric

发布后 30 天内：
- Pro user 留存率 +10pp（从当前 baseline）
- Twitter/HN launch post 触达 5K+ 开发者
- "yield score" 出现在 1+ 第三方推荐文章

---

## 二、Feature scope (MVP)

### What it shows

OverviewTab 加一个新卡片 **"Yield Score"**，按时段（7天/30天）分 provider 显示：

```
┌─────────────────────────────────────┐
│  Yield Score · Last 30 days         │
├─────────────────────────────────────┤
│  Claude        $42.10 → 89 commits  │
│                $0.47 / commit       │
│                                     │
│  Cursor        $20.00 → 12 commits  │
│                $1.67 / commit ⚠️    │
│                                     │
│  Codex         $15.00 → 47 commits  │
│                $0.32 / commit ⭐    │
│                                     │
│  [View detail →]                    │
└─────────────────────────────────────┘
```

⭐ = best yield in range；⚠️ = >2x average (potentially poor ROI)。

点 "View detail" 跳到独立 YieldScoreView，显示：
- 每个 commit 的归属 (provider, session id, cost, timestamp)
- 时间趋势图（cost/commit over time）
- Per-project breakdown（哪些 repo 用 AI 最多）

### What it does NOT show in MVP

- **PR-level grouping**（Phase 2）：commit 是更原子的；PR 需要 git remote/GitHub API。
- **LOC metrics** (`+150 -23`)：noisy proxy，更易误导。先用 com

*[truncated — see source for full prompt]*