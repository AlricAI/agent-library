---
name: API CLIENTS
description: Specifications for all external API integrations.
model: claude-sonnet-4-5
---
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
- `500/503` → exponential backoff (2s, 4s, 8s), max 3 retries, then fail task

### 1.2 Fetch Market Resolution

```
GET /markets/{condition_id}
```

**Key response fields:**
```json
{
  "condition_id": "0x...",
  "question": "Will BTC be higher in 5 minutes?",
  "end_date_iso": "2024-01-15T12:05:00Z",
  "active": false,
  "closed": true,
  "tokens": [
    {"token_id": "...", "outcome": "Yes", "winner": true},
    {"token_id": "...", "outcome": "No",  "winner": false}
  ]
}
```

**Parsing:**
```python
resolution = {
    "market_id":          data["condition_id"],
    "platform":           "polymarket",
    "resolved_at":        datetime.fromisoformat(data["end_date_iso"]),
    "outcome_yes":        next(t for t in data["tokens"] if t["outcome"] == "Yes")["winner"],
    "resolution_source":  "platform_api",
    "disputed":           False,
}
```

### 1.3 Discover Active BTC 5-Min Markets

```
GET /markets
  ?active=true
  &closed=false
  &category=Crypto
  &tag=BTC
  &limit=100
```

Filter results where `question` matches the pattern: `r"Will Bitcoin.*\d+ minutes?"` (case-insensitive).

Add discovered market IDs to `config/markets.yaml` and insert into `markets` table.

### 1.4 Polygon RPC Verification (Optional, Phase 0)

To verify resolution on-chain via the UMA oracle:

```python
from web3 import Web3

w3 = Web3(Web3.HTTPProvider(os.getenv("POLYGON_RPC_URL")))
uma_contract = w3.eth.contract(
    address=UMA_CONTRACT_ADDRESS,  # from config/markets.yaml
    abi=UMA_ABI,                   # from config/abis/uma_ctf_adapter.json
)
# Check settlement:
resolved_price = uma_contract.functions.settledPrice(condition_id_bytes).call()
# resolved_price = 1e18 if YES won, 0 if NO won
outcome_yes_onchain = resolved_price > 0
```

If on-chain outcome ≠ API outcome: set `disputed = True` in `resolutions` table.

---

## 2. Binance REST API (via ccxt)

**Library:** `ccxt.binance` (async)
**Authentication:** `BINANCE_API_KEY` + `BINANCE_API_SECRET`
**Rate limit:** 1200 weight/minute (1s candles = 1 weight per request, max 1000 candles per request)
**Client file:** `ingestion/binance.py`

### 2.1 Fetch 1-Second OHLCV

```python
import ccxt.async_support as ccxt

exchange = ccxt.binance({
    "apiKey":       os.getenv("BINANCE_API_KEY"),
    "secret":       os.getenv("BINANCE_API_SECRET"),
    "enableRateLimit": True,
})

# Fetch 1-second candles for a time range
candles = await exchange.fetch_ohlcv(
    symbol="BTC/USDT",
    timeframe="1s",
    since=int(start_ts.timestamp() * 1000),  # milliseconds
    limit=1000,
    params={"endTime": int(end_ts.timestamp() * 1000)},
)
# Returns: [[timestamp_ms, open, high, low, close, volume], ...]
```

**For a 5-minute slot** (300s), fetch window `[t0 − 10s, t_close + 10s]` = 320s = 320 candles. Fits in a single request (limit=1000).

**Parsing:**
```python
def candles_to_df(candles: list) -> pl.DataFrame:
    return pl.DataFrame({
        "ts_ms":  [c[0] for c in candles],
        "open":   [c[1] for c in candles],
        "high":   [c[2] for c in candles],
        "low":    [c[3] for c in candles],
        "close":  [c[4] for c in candles],
        "volume": [c[5] for c in candles],
    }).with_columns(
        pl.from_epoch("ts_ms", time_unit="ms").alias("ts_utc")
    )
```

**Slot alignment:**
```python
def get_slot_prices(candles_df: pl.DataFrame, t0: datetime, t_close: datetime) -> dict:
    at_t0     = candles_df.filter(pl.col("ts_utc") >= t0).head(1)
    at_close  = candles_df.filter(pl.col("ts_utc") <= t_close).tail(1)
    return {
        "btc_price_open":  at_t0["open"][0],
        "btc_price_close": at_close["close"][0],
    }
```

### 2.2 Fallback to 1-Minute Candles

If 1s candles are not available (Binance limits 1s data to ~30 days history):

```python
candles_1m = await exchange.fetch_ohlcv("BTC/USDT", "1m", since=..., limit=10)
# Interpolate linearly between minute boundaries
# Mark interpolated=True in reference_prices
```

**Linear interpolation:**
```python
# For a slot opening 42 seconds into a 1-minute candle:
# price = candle_open + 42/60 * (candle_close - candle_open)
fraction = (t0_utc.second) / 60.0
btc_price_open = candle["open"] + fraction * (candle["close"] - candle["open"])
```

---

## 3. Future APIs (Phase 1 Stubs)

These are not implemented in Phase 0. Document them here so the coding agent knows what the `BaseIngestor` interface must eventually support.

### 3.1 Kalshi REST API

**Base URL:** `https://trading-api.kalshi.com/trade-api/v2`
**Authentication:** Bearer JWT (obtained via `/login` endpoint)
**Client file (Phase 1):** `ingestion/kalshi.py`

Key endpoints needed:
- `GET /markets/{ticker}/trades` — trade history
- `GET /markets/{ticker}` — market resolution

Note: Kalshi uses a maker-taker fee model, not a fixed % on winnings. Fee calculation:
```
fee = max(maker_fee_rate, taker_fee_rate) × size_usd
# Currently: maker = 0, taker = 0.07 for most markets
```
This requires a different `fee_rate` computation than Polymarket.

### 3.2 Manifold Markets API

**Base URL:** `https://api.manifold.markets/v0`
**Authentication:** API key in `Authorization` header
**Client file (Phase 1):** `ingestion/manifold.py`

Key differences from Polymarket:
- AMM pricing (not CLOB): `q0` derived from AMM price formula
- Play-money: `size_usd = mana_amount × MANA_USD_RATE` (use 1:100 conversion)
- Fee = 0 for most markets (important: IER baseline use case)
- No intra-slot tick data for most markets; q* approximated from question-level probability history

### 3.3 Metaculus API

**Base URL:** `https://www.metaculus.com/api2`
**Authentication:** API key in `Authorization` header
**Client file (Phase 1):** `ingestion/metaculus.py`

Key differences:
- Aggregation platform, not a trading exchange — no CLOB, no q*
- q₀ = community prediction at question open; q* not directly available (use time-series minimum of community prediction as proxy)
- Used for long-horizon classes: M1, M2, S1
- Resolutions from Metaculus are authoritative; no on-chain verification

### 3.4 Betfair Exchange API

**Base URL:** `https://api.betfair.com/exchange/betting/rest/v1.0`
**Authentication:** OAuth2 application key + session token
**Client file (Phase 1):** `ingestion/betfair.py`

Key differences:
- P2P exchange (not market maker): odds are other bettors' prices
- Commission model: 2–5% of NET WINNINGS per market (not gross)
- `q₀` derived from back/lay odds: `q0 = 1 / best_back_odds` (approximate)
- API requires UK identity verification; may require separate API key from a UK entity

---

## 4. Client Implementation Pattern

All ingestors must follow this async pattern:

```python
# ingestion/polymarket.py (example)
import httpx
import asyncio
from datetime import date, datetime, timezone
from ingestion.base import BaseIngestor, Resolution
import polars as pl
import logging

logger = logging.getLogger(__name__)

class PolymarketIngestor(BaseIngestor):

    BASE_URL = "https://clob.polymarket.com"
    RATE_LIMIT_RPS = 10

    def __init__(self, api_key: str):
        self._api_key = api_key
        self._semaphore = asyncio.Semaphore(self.RATE_LIMIT_RPS)
        self._client: httpx.AsyncClient | None = None

    async def __aenter__(self) -> "PolymarketIngestor":
        self._client = httpx.AsyncClient(
            headers={"Authorization": f"Bearer {self._api_key}"},
            timeout=30.0,
        )
        return self

    async def __aexit__(self, *_):
        if self._client:
            await self._client.aclose()

    async def _get(self, path: str, params: dict = {}) -> dict:
        """Single authenticated GET with rate limiting and retry."""
        for attempt in range(3):
            async with self._semaphore:
                try:
                    r = await self._client.get(f"{self.BASE_URL}{path}", params=params)
                    r.raise_for_status()
                    return r.json()
                except httpx.HTTPStatusError as e:
                    if e.response.status_code == 429:
                        wait = float(e.response.headers.get("Retry-After", 2 ** attempt))
                        logger.warning("Rate limited, waiting %.1fs", wait)
                        await asyncio.sleep(wait)
                        continue
                    if e.response.status_code == 404:
                        raise  # Don't retry 404
                    logger.error("HTTP error on attempt %d: %s", attempt + 1, e)
                    await asyncio.sleep(2 ** attempt * (1 + 0.2 * (asyncio.get_event_loop().time() % 1)))
        raise RuntimeError(f"Failed after 3 attempts: GET {path}")

    async def fetch_trades(self, market_id: str, date: date) -> pl.DataFrame:
        """Fetch all trades for a market on a given date."""
        # ... implementation per Section 1.1 above
        ...

    async def fetch_resolution(self, market_id: str) -> Resolution:
        """Fetch resolution for a market."""
        # ... implementation per Section 1.2 above
        ...

    async def get_market_ids(self, class_code: str, date: date) -> list[str]:
        """Get all active market IDs for a class on a date."""
        # ... implementation per Section 1.3 above
        ...
```

Usage from pipeline stage:

```python
async with PolymarketIngestor(api_key=os.getenv("POLYMARKET_API_KEY")) as client:
    trades_df = await client.fetch_trades(market_id, target_date)
    resolution = await client.fetch_resolution(market_id)
```