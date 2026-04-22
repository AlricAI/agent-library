# Route Analytics Examples

> This document provides practical examples for working with the route analytics system, including SQL queries for monitoring, debugging, and analysis.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Route Analytics - Example Queries and Usage

This document provides practical examples for working with the route analytics system, including SQL queries for monitoring, debugging, and analysis.

## Table of Contents
- [Quick Start Examples](#quick-start-examples)
- [Monitoring Queries](#monitoring-queries)
- [Cache Analysis Queries](#cache-analysis-queries)
- [Performance Analysis](#performance-analysis)
- [Debugging and Troubleshooting](#debugging-and-troubleshooting)
- [API Usage Examples](#api-usage-examples)
- [CLI Usage Examples](#cli-usage-examples)

## Quick Start Examples

### Check if Data is Flowing

```sql
-- Check recent raw events (should see data from last 10 minutes)
SELECT COUNT(*), MAX(timestamp) as latest_event
FROM route_analytics
WHERE timestamp > NOW() - INTERVAL '15 minutes';

-- Check hourly aggregations (should see data from last few hours)
SELECT COUNT(*), MAX(timestamp) as latest_hour
FROM route_analytics_hourly
WHERE timestamp > NOW() - INTERVAL '24 hours';
```

### View Recent Requests

```sql
-- Last 100 requests with their performance
SELECT
    timestamp,
    route,
    method,
    duration_ms,
    status_code,
    user_id
FROM route_analytics
ORDER BY timestamp DESC
LIMIT 100;
```

### Top 10 Slowest Routes (Last 24 Hours)

```sql
SELECT
    route,
    method,
    AVG(avg_duration_ms)::INTEGER as avg_latency,
    AVG(p95_duration_ms)::INTEGER as p95_latency,
    AVG(p99_duration_ms)::INTEGER as p99_latency,
    SUM(total_requests) as total_requests
FROM route_analytics_hourly
WHERE timestamp > NOW() - INTERVAL '24 hours'
GROUP BY route, method
ORDER BY avg_latency DESC
LIMIT 10;
```

## Monitoring Queries

### Data Freshness Check

```sql
-- Check how fresh the data is in both tables
SELECT
    'route_analytics' as table_name,
    COUNT(*) as total_rows,
    MAX(timestamp) as latest_timestamp,
    NOW() - MAX(timestamp) as data_age
FROM route_analytics
UNION ALL
SELECT
    'route_analytics_hourly' as table_name,
    COUNT(*) as tot

*[truncated — see source for full prompt]*