# 012 Tokenterminal Source

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 012 — TokenTerminal Source Adapter (Protocol Revenue/Earnings)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** Real implementations only.
2. **TypeScript strict mode** — no `any`, no `@ts-ignore`.
3. **Always kill terminals** after commands complete.
4. **Always commit and push** as `nirholas`.
5. **If close to hallucinating** — stop and tell the prompter.
6. **Run `npx tsc --noEmit` and `npx vitest run`** after changes.

---

## Task

Build `src/sources/tokenterminal.ts` — the adapter for Token Terminal, which provides protocol-level financial metrics: revenue, fees, earnings, P/S ratios, active users, and developer activity.

### API Base URL

```
https://api.tokenterminal.com/v2     # v2 REST API
# Auth: Authorization: Bearer {key}
# Env: TOKENTERMINAL_API_KEY
```

### Requirements

#### 1. Zod Schemas

- `TTProject` — project_id, name, symbol, category, market_cap, fully_diluted_valuation, revenue_30d, revenue_annualized, fees_30d, fees_annualized, earnings_30d, tvl, active_users_30d, price_to_sales, price_to_fees, price_to_earnings, token_incentives_30d
- `TTMetricTimeseries` — timestamp, value pairs
- `TTMarketSector` — category, total_revenue, total_fees, total_tvl, project_count, top_projects[]
- `TTFinancialStatement` — revenue, fees, earnings, token_incentives, active_users (daily, 7d, 30d, 90d, 180d, 365d)

#### 2. Exported Functions

| Function | Endpoint | Cache TTL |
|----------|----------|-----------|
| `getProjects(limit?)` | `/projects` | 120s |
| `getProjectDetail(id)` | `/projects/{id}` | 120s |
| `getProjectMetrics(id, metric, interval?)` | `/projects/{id}/metrics/{metric}` | 120s |
| `getProjectFinancials(id)` | `/projects/{id}/financials` | 120s |
| `getMarketSectors()` | `/market-sectors` | 300s |
| `getTopByRevenue(limit?)` | Sort

*[truncated — see source for full prompt]*