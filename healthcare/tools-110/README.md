# TOOLS

> ## Available Tools
- Bash (SSH to Mini for process health, Forge API queries)
- File read/write (agent instruction files, reports)
- Forge API (issues

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — MCM Forge Factory Analyst

## Available Tools
- Bash (SSH to Mini for process health, Forge API queries)
- File read/write (agent instruction files, reports)
- Forge API (issues, runs, agents, costs)
- Supabase SQL (direct queries for analytics)

## Forge Database Queries

```sql
-- Agent performance (last 24h)
SELECT a.name, count(*) as runs,
  count(*) FILTER (WHERE r.status = 'succeeded') as ok,
  count(*) FILTER (WHERE r.status = 'failed') as fail,
  sum(r.cost_usd)::numeric(10,2) as cost
FROM forge.runs r JOIN forge.agents a ON r.agent_id = a.id
WHERE r.created_at > now() - interval '24 hours'
GROUP BY a.name ORDER BY runs DESC;

-- Failure patterns (last 7 days)
SELECT a.name, LEFT(r.error, 100) as error, count(*) 
FROM forge.runs r JOIN forge.agents a ON r.agent_id = a.id
WHERE r.status = 'failed' AND r.created_at > now() - interval '7 days'
GROUP BY a.name, LEFT(r.error, 100) ORDER BY count DESC LIMIT 10;

-- Stuck issues (hours since last update)
SELECT i.identifier, i.title, i.status, a.name,
  EXTRACT(EPOCH FROM (now() - i.updated_at))/3600 as hours_stuck
FROM forge.issues i LEFT JOIN forge.agents a ON i.assignee_agent_id = a.id
WHERE i.status NOT IN ('done', 'cancelled')
ORDER BY hours_stuck DESC LIMIT 10;

-- Daily throughput
SELECT date_trunc('day', r.finished_at)::date as day,
  count(*) FILTER (WHERE r.status = 'succeeded') as ok,
  count(*) FILTER (WHERE r.status = 'failed') as fail,
  sum(r.cost_usd)::numeric(10,2) as cost
FROM forge.runs r WHERE r.finished_at > now() - interval '7 days'
GROUP BY day ORDER BY day;

-- Queue depth right now
SELECT status, count(*) FROM forge.runs 
WHERE status IN ('queued', 'running') GROUP BY status;
```

## Mini Health Check
```bash
ssh dirtsyncmini@100.125.184.57 'echo "=== Orchestrator ===" && curl -s http://127.0.0.1:3200/api/health && echo "" && echo "=== Simulator ===" && xcrun simctl list devices booted && echo "=== Disk ===" && df -h / | tail -1 && echo "=== Active Processes ===" && ps aux | gr

*[truncated — see source for full prompt]*