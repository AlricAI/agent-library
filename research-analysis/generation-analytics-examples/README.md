# Generation Analytics Examples

> This document provides practical examples for querying generation analytics data, including direct SQL queries and API usage examples.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Generation Analytics Examples

This document provides practical examples for querying generation analytics data, including direct SQL queries and API usage examples.

## Table of Contents

1. [API Examples](#api-examples)
2. [Direct SQL Queries](#direct-sql-queries)
3. [Common Analysis Patterns](#common-analysis-patterns)
4. [Data Pipeline](#data-pipeline)

## API Examples

### Basic Dashboard Overview

Get a quick summary of generation activity for the last 7 days:

```bash
curl "http://localhost:8001/api/v1/analytics/generation/overview?days=7"
```

```python
import requests

response = requests.get(
    "http://localhost:8001/api/v1/analytics/generation/overview",
    params={"days": 7}
)
data = response.json()

print(f"Success rate: {data['success_rate_pct']:.1f}%")
print(f"Total requests: {data['total_requests']}")
print(f"P95 latency: {data['p95_duration_ms']}ms")
```

### Time-Series Analysis

Get hourly trends to visualize generation patterns:

```bash
curl "http://localhost:8001/api/v1/analytics/generation/trends?days=7&interval=hourly"
```

```python
import requests
import pandas as pd
import matplotlib.pyplot as plt

# Fetch trends data
response = requests.get(
    "http://localhost:8001/api/v1/analytics/generation/trends",
    params={"days": 7, "interval": "hourly"}
)
data = response.json()

# Convert to DataFrame for analysis
df = pd.DataFrame(data['data_points'])
df['timestamp'] = pd.to_datetime(df['timestamp'])

# Plot success rate over time
plt.figure(figsize=(12, 6))
plt.plot(df['timestamp'], df['success_rate'], marker='o')
plt.xlabel('Time')
plt.ylabel('Success Rate')
plt.title('Generation Success Rate - Last 7 Days')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### User-Specific Analytics

Analyze generation history for a specific user:

```bash
USER_ID="550e8400-e29b-41d4-a716-446655440000"
curl "http://localhost:8001/api/v1/analytics/generation/users/${USER_ID}?days=30"
```

```python
import requests

user_id = "550e8400-e29b-41

*[truncated — see source for full prompt]*