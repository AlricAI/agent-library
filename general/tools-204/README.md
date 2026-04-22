# TOOLS

> Reference SQL, regex patterns, and state schemas.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — Harness Doctor

Reference SQL, regex patterns, and state schemas.

---

## Core SQL Queries

### Failed runs last 7 days, joined with agent
```sql
SELECT
  r.id, r.agent_id, a.name as agent_name, r.error_code,
  substring(r.error, 1, 200) as error_head,
  substring(r.stderr_excerpt, 1, 300) as stderr_head,
  r.cost_usd, r.created_at,
  r.context_snapshot->>'issueId' as issue_id,
  r.context_snapshot->>'issue_title' as issue_title
FROM forge.runs r
JOIN forge.agents a ON r.agent_id = a.id
WHERE r.status = 'failed'
  AND r.created_at > now() - interval '7 days'
ORDER BY r.created_at DESC
LIMIT 500;
```

### Count failures by error_code across agents
```sql
SELECT
  a.name as agent, r.error_code,
  count(*) as occurrences,
  sum(r.cost_usd)::numeric(10,2) as total_cost,
  array_agg(r.id ORDER BY r.created_at DESC) FILTER (WHERE r.created_at > now() - interval '24 hours') as recent_24h,
  array_agg(DISTINCT r.context_snapshot->>'issueId') as affected_issues
FROM forge.runs r
JOIN forge.agents a ON r.agent_id = a.id
WHERE r.status = 'failed'
  AND r.created_at > now() - interval '7 days'
  AND r.error_code IS NOT NULL
GROUP BY a.name, r.error_code
HAVING count(*) >= 2
ORDER BY total_cost DESC, occurrences DESC;
```

### Stuck handoffs — issues in the same status > 4 hours
```sql
SELECT
  i.id, i.title, i.status, a.name as assignee,
  EXTRACT(EPOCH FROM (now() - i.updated_at))/3600 as hours_stuck
FROM forge.issues i
LEFT JOIN forge.agents a ON i.assignee_agent_id = a.id
WHERE i.status IN ('in_progress', 'in_review', 'todo')
  AND i.updated_at < now() - interval '4 hours'
  AND i.company_id = '170ebe36-d689-4f15-91f1-7474df6c98cd'  -- adjust per company
ORDER BY hours_stuck DESC
LIMIT 20;
```

### Layer 1 dedup — existing [harness] issues
```sql
SELECT id, identifier, title, status, created_at
FROM forge.issues
WHERE title ILIKE '[harness]%'
  AND status NOT IN ('done', 'cancelled', 'approved')
ORDER BY created_at DESC;
```

### Layer 2 dedup — keyword fuzzy m

*[truncated — see source for full prompt]*