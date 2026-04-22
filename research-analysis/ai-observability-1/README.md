# Ai Observability

> Production AI systems require deep observability into model performance, cost, and data quality.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Observability in Production

Production AI systems require deep observability into model performance, cost, and data quality. This pattern covers instrumentation, alerting, and data quality monitoring for LLM-powered applications.

## Key Metrics

| Metric | Measures | Healthy | Alert |
|--------|----------|---------|-------|
| **TTFT** (Time to First Token) | Model latency before streaming begins | <500ms | >2s |
| **TPS** (Tokens Per Second) | Throughput of model inference | >50 | <20 |
| **E2E Latency** | Full request roundtrip (network + model + retrieval) | <2s | >5s |
| **Prompt Tokens** | Input token count per request | <4k | >8k |
| **Completion Tokens** | Output token count per request | <2k | >4k |
| **Cost Per Request** | USD spent per inference | track baseline | 3× baseline |
| **Error Rate** | % of requests that fail or timeout | <1% | >5% |
| **Cache Hit Rate** | Requests served from cache (semantic cache, KV cache, or response cache) | >40% | <20% |

Track these metrics per model, per endpoint, and aggregated. Set up dashboards that update every 60s for real-time visibility.

## Data Quality Monitoring

### Input Drift Detection

Monitor whether input embeddings or feature distributions shift over time, indicating data quality degradation or out-of-distribution requests.

1. **Baseline**: embed a sample of requests from the first week; compute centroid and covariance matrix
2. **Monitor**: every 24 hours, compute KL divergence or Kolmogorov-Smirnov test statistic between current day's embeddings and baseline
3. **Alert threshold**: KS test p-value < 0.05 (statistically significant drift) or cosine similarity of daily centroid to baseline < 0.95
4. **Root cause**: check for new user cohorts, seasonal patterns, or degraded upstream data quality

### Output Quality Scoring

Use an LLM-as-judge to automatically score a sample of outputs (10% of production traffic, capped at 100 evals/day to manage cost).

```
Sample Request
├─ Criteria: relevance, f

*[truncated — see source for full prompt]*