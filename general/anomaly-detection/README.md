# ANOMALY DETECTION

> > Real-time statistical anomaly detection across 16 event types using Modified Z-Score, EWMA, and rate-of-change algorithms.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Anomaly Detection

> Real-time statistical anomaly detection across 16 event types using Modified Z-Score, EWMA, and rate-of-change algorithms.

---

## Table of Contents

- [Overview](#overview)
- [Algorithms](#algorithms)
- [Anomaly Types](#anomaly-types)
- [Configuration](#configuration)
- [Data Flow](#data-flow)
- [Processors](#processors)
- [API Endpoints](#api-endpoints)
- [WebSocket Alerts](#websocket-alerts)
- [State Persistence](#state-persistence)
- [Extending the Engine](#extending-the-engine)

---

## Overview

The anomaly detection engine continuously monitors incoming data from all 37 data sources and detects statistically significant deviations from normal patterns. When an anomaly is detected, it is:

1. **Broadcast** to WebSocket clients on the `alerts` topic in real-time
2. **Logged** to BigQuery (`anomaly_events` table) for historical analysis
3. **Stored** in an in-memory ring buffer (500 most recent) for the REST API
4. **Streamed** via Server-Sent Events for real-time dashboard integration

**Source files:**
- `src/lib/anomaly.ts` — Core engine, SlidingWindow, detector configs
- `src/lib/anomaly-processors.ts` — Data feed processors and handler registration
- `src/routes/anomaly.ts` — REST API and SSE endpoints

---

## Algorithms

### Modified Z-Score (MAD)

The primary detection algorithm uses the **Median Absolute Deviation (MAD)** instead of standard deviation, making it robust to outliers that would skew standard z-scores.

$$Z_{modified} = \frac{0.6745 \times (x - \tilde{x})}{MAD}$$

Where:
- $x$ = current value
- $\tilde{x}$ = median of the sliding window
- $MAD$ = median of absolute deviations from the median
- $0.6745$ = 75th percentile of the standard normal distribution (makes the score comparable to regular z-scores)

**Why MAD over standard deviation?** Crypto markets have fat-tailed distributions with extreme outliers. Standard deviation is heavily influenced by these outliers, making the z-score unreliable. MAD ignores outliers

*[truncated — see source for full prompt]*