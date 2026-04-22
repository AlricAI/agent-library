# TOOLS

> SQL queries, thresholds, baseline schema.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — Cost Regression Watcher

SQL queries, thresholds, baseline schema.

---

## Core SQL Queries

### Total spend last 24h
```sql
SELECT
  coalesce(sum(cost_usd), 0)::numeric(10,2) as total_spend,
  count(*) as run_count,
  count(*) FILTER (WHERE status = 'succeeded') as success_count,
  count(*) FILTER (WHERE status = 'failed') as failure_count,
  count(*) FILTER (WHERE cost_usd IS NULL) as null_cost_count
FROM forge.runs
WHERE finished_at > now() - interval '24 hours';
```

### Cost by adapter
```sql
SELECT
  a.adapter_type,
  count(r.*) as run_count,
  coalesce(sum(r.cost_usd), 0)::numeric(10,2) as total_cost
FROM forge.runs r
JOIN forge.agents a ON r.agent_id = a.id
WHERE r.finished_at > now() - interval '24 hours'
GROUP BY a.adapter_type
ORDER BY total_cost DESC;
```

### Top 5 spending agents last 24h
```sql
SELECT
  a.name, a.adapter_type,
  count(r.*) as runs,
  coalesce(sum(r.cost_usd), 0)::numeric(10,2) as cost,
  coalesce(avg(r.cost_usd), 0)::numeric(10,2) as avg_cost_per_run
FROM forge.runs r
JOIN forge.agents a ON r.agent_id = a.id
WHERE r.finished_at > now() - interval '24 hours'
GROUP BY a.id, a.name, a.adapter_type
ORDER BY cost DESC
LIMIT 5;
```

### Cost per shipped feature
```sql
WITH shipped_issues AS (
  SELECT id FROM forge.issues
  WHERE status = 'done'
    AND completed_at > now() - interval '24 hours'
),
issue_costs AS (
  SELECT
    (r.context_snapshot->>'issueId')::uuid as issue_id,
    sum(r.cost_usd) as total_cost
  FROM forge.runs r
  WHERE r.context_snapshot->>'issueId' IS NOT NULL
    AND (r.context_snapshot->>'issueId')::uuid IN (SELECT id FROM shipped_issues)
  GROUP BY (r.context_snapshot->>'issueId')
)
SELECT
  count(*) as shipped_count,
  coalesce(sum(total_cost), 0)::numeric(10,2) as total_cost,
  coalesce(avg(total_cost), 0)::numeric(10,2) as avg_cost_per_feature
FROM issue_costs;
```

### Failed-run percentage last 24h
```sql
SELECT
  100.0 * count(*) FILTER (WHERE status = 'failed') / nullif(count(*), 0) as failed_pc

*[truncated — see source for full prompt]*