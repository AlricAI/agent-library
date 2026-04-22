# Trader

> """
Trader Agent - Commodity ETF Trading

Strategy:
- Buy SGOL/CPER on 2-3% pullback from recent highs
- Buy SCO (inverse oil) when oil spikes
- Exit:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Trader Agent - Commodity ETF Trading

Strategy:
- Buy SGOL/CPER on 2-3% pullback from recent highs
- Buy SCO (inverse oil) when oil spikes
- Exit: +5% profit, -5% stop, or end of day

State stored in Supabase (amber_state table).
Designed to run on Railway via scheduler.
"""

import json
import sys
import urllib.request
import urllib.parse
from datetime import datetime, timedelta
from typing import Optional
import pytz

from alpaca_client import AlpacaClient, is_market_open, get_market_status
from config import (
    GOLD_SYMBOL,
    OIL_INVERSE_SYMBOL,
    COPPER_SYMBOL,
    BUDGET_PER_SIDE,
    PULLBACK_THRESHOLD,
    PROFIT_TARGET,
    STOP_LOSS,
    LOOKBACK_DAYS,
    SUPABASE_URL,
    SUPABASE_KEY,
    VERBOSE,
)

# Timezone
ET = pytz.timezone('America/New_York')
PT = pytz.timezone('America/Los_Angeles')


# =============================================================================
# SUPABASE STATE MANAGEMENT
# =============================================================================

def supabase_request(method: str, endpoint: str, data: Optional[dict] = None) -> dict:
    """Make a request to Supabase REST API."""
    if not SUPABASE_URL or not SUPABASE_KEY:
        raise ValueError("SUPABASE_URL and SUPABASE_KEY required")

    url = f"{SUPABASE_URL}/rest/v1/{endpoint}"
    headers = {
        "apikey": SUPABASE_KEY,
        "Authorization": f"Bearer {SUPABASE_KEY}",
        "Content-Type": "application/json",
        "Prefer": "return=representation",
    }

    try:
        if data:
            payload = json.dumps(data).encode()
            req = urllib.request.Request(url, data=payload, method=method, headers=headers)
        else:
            req = urllib.request.Request(url, method=method, headers=headers)

        with urllib.request.urlopen(req, timeout=10) as response:
            return json.loads(response.read().decode())
    except urllib.error.HTTPError as e:
        error_body = e.read().decode() if e.fp else str(e)
        print(f"[

*[truncated — see source for full prompt]*