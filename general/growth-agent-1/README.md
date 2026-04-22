# Growth Agent

> from __future__ import annotations

"""Growth Agent

Implements a growth-focused valuation methodology.
"""

import json
import statistics
from langch

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""Growth Agent

Implements a growth-focused valuation methodology.
"""

import json
import statistics
from langchain_core.messages import HumanMessage
from src.graph.state import AgentState, show_agent_reasoning
from src.utils.progress import progress
from src.utils.api_key import get_api_key_from_state
from src.tools.api import (
    get_financial_metrics,
    get_insider_trades,
)

def growth_analyst_agent(state: AgentState, agent_id: str = "growth_analyst_agent"):
    """Run growth analysis across tickers and write signals back to `state`."""

    data = state["data"]
    end_date = data["end_date"]
    tickers = data["tickers"]
    api_key = get_api_key_from_state(state, "FINANCIAL_DATASETS_API_KEY")
    growth_analysis: dict[str, dict] = {}

    for ticker in tickers:
        progress.update_status(agent_id, ticker, "Fetching financial data")

        # --- Historical financial metrics ---
        financial_metrics = get_financial_metrics(
            ticker=ticker,
            end_date=end_date,
            period="ttm",
            limit=12, # 3 years of ttm data
            api_key=api_key,
        )
        if not financial_metrics or len(financial_metrics) < 4:
            progress.update_status(agent_id, ticker, "Failed: Not enough financial metrics")
            continue
        
        most_recent_metrics = financial_metrics[0]

        # --- Insider Trades ---
        insider_trades = get_insider_trades(
            ticker=ticker,
            end_date=end_date,
            limit=1000,
            api_key=api_key
        )

        # ------------------------------------------------------------------
        # Tool Implementation
        # ------------------------------------------------------------------
        
        # 1. Historical Growth Analysis
        growth_trends = analyze_growth_trends(financial_metrics)
        
        # 2. Growth-Oriented Valuation
        valuation_metrics = analyze_valuation(most_re

*[truncated — see source for full prompt]*