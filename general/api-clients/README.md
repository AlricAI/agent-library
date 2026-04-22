# API CLIENTS

> Specifications for all external API integrations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API_CLIENTS.md — API Integration Specifications

Specifications for all external API integrations. Each section defines the exact endpoints, authentication, rate limits, data parsing, and error handling for one data source.

---

## 1. Polymarket CLOB API

**Base URL:** `https://clob.polymarket.com`
**Authentication:** Bearer token via `POLYMARKET_API_KEY` env var
**Rate limit:** ~10 requests/second (unpublished; implement conservative limiter)
**Client file:** `ingestion/polymarket.py`

### 1.1 Fetch CLOB Trade History

```
GET /trades
  ?market={condition_id}
  &after={unix_timestamp_ms}
  &before={unix_timestamp_ms}
  &limit=1000
```

**Response schema (one trade object):**

```json
{
  "id": "0x...",
  "market": "0x...",           // condition_id
  "outcome": "Yes",            // "Yes" | "No"
  "side": "BUY",               // "BUY" | "SELL"
  "price": "0.52",             // string float ∈ (0, 1)
  "size": "100",               // string — units in USDC (6 decimals)
  "timestamp": 1700000000000,  // milliseconds UTC
  "transactionHash": "0x..."   // Polygon tx hash
}
```

**Parsing to `trades` schema:**

```python
trade = {
    "trade_id":   row["id"],
    "market_id":  row["market"],
    "platform":   "polymarket",
    "ts_utc":     datetime.fromtimestamp(row["timestamp"] / 1000, tz=timezone.utc),
    "token":      "yes" if row["outcome"] == "Yes" else "no",
    "side":       row["side"].lower(),
    "price":      float(row["price"]),
    "size_usd":   float(row["size"]) / 1e6,   # USDC uses 6 decimal places
    "tx_hash":    row["transactionHash"],
    "raw_json":   row,
}
```

**Pagination:** The API returns up to 1000 results per request. If `len(results) == 1000`, fetch next page with `after={last_timestamp}`. Continue until `len(results) < 1000`.

**Error handling:**
- `429 Too Many Requests` → wait `retry_after` header seconds + jitter, retry
- `404 Not Found` → market does not exist; add to exclusion list, do not retry
- `500/503` → exponential backoff (

*[truncated — see source for full prompt]*