---
name: Config
description: """
Trader Agent Configuration

Commodity ETF trading strategy:
- Gold (SGOL), Oil inverse (SCO), Copper (CPER)
- Entry: Buy on 2% pullback from recen
model: claude-sonnet-4-5
---
"""
Trader Agent Configuration

Commodity ETF trading strategy:
- Gold (SGOL), Oil inverse (SCO), Copper (CPER)
- Entry: Buy on 2% pullback from recent high
- Exit: +5% profit, -5% stop loss, or end of day

Deployed on Railway, state stored in Supabase.
"""

import os
from pathlib import Path

# Load environment from sms-bot/.env.local (for local development)
try:
    from dotenv import load_dotenv
    env_path = Path(__file__).parent.parent.parent / ".env.local"
    if env_path.exists():
        load_dotenv(env_path, override=False)
except ImportError:
    pass  # dotenv not required on Railway

# ============ TRADING MODE ============
# Set to "live" to enable real money trading
# Set to "paper" for paper trading
TRADING_MODE = os.getenv("TRADING_MODE", "live")

# ============ ASSETS ============
GOLD_SYMBOL = "SGOL"      # Physical gold ETF (low expense ratio)
OIL_INVERSE_SYMBOL = "SCO"  # 2x inverse oil ETF
COPPER_SYMBOL = "CPER"    # United States Copper Index Fund

# ============ POSITION SIZING ============
BUDGET_PER_SIDE = float(os.getenv("TRADER_BUDGET", "250.0"))  # $ per position
MAX_POSITION = BUDGET_PER_SIDE

# ============ ENTRY TRIGGERS ============
PULLBACK_THRESHOLD = -0.02  # 2% pullback from recent high

# ============ EXIT RULES ============
PROFIT_TARGET = 0.05   # +5%
STOP_LOSS = -0.05      # -5%
EOD_EXIT = True        # Exit at end of day

# ============ ANALYSIS ============
LOOKBACK_DAYS = 10     # Days to look back for recent high

# ============ ALPACA ============
ALPACA_API_KEY = os.getenv("ALPACA_API_KEY")
ALPACA_SECRET_KEY = os.getenv("ALPACA_SECRET_KEY")

# ============ SUPABASE ============
SUPABASE_URL = os.getenv("SUPABASE_URL") or os.getenv("NEXT_PUBLIC_SUPABASE_URL")
SUPABASE_KEY = os.getenv("SUPABASE_SERVICE_KEY") or os.getenv("SUPABASE_SERVICE_ROLE_KEY")

# ============ LOGGING ============
VERBOSE = os.getenv("TRADER_VERBOSE", "true").lower() == "true"


def print_config():
    """Print current configuration."""
    mode_emoji = "🔴 LIVE" if TRADING_MODE == "live" else "📝 PAPER"
    print(f"""
╔══════════════════════════════════════════════════════════════╗
║  TRADER AGENT - Commodity ETF Strategy                       ║
╠══════════════════════════════════════════════════════════════╣
║  Trading Mode:     {mode_emoji}
║  Gold Asset:       {GOLD_SYMBOL}
║  Oil Asset:        {OIL_INVERSE_SYMBOL}
║  Copper Asset:     {COPPER_SYMBOL}
║  Budget/Side:      ${BUDGET_PER_SIDE}
║  Pullback Entry:   {abs(PULLBACK_THRESHOLD)*100}%
║  Profit Target:    +{PROFIT_TARGET*100}%
║  Stop Loss:        {STOP_LOSS*100}%
║  EOD Exit:         {EOD_EXIT}
║  Alpaca Key:       {"✓" if ALPACA_API_KEY else "✗"}
║  Supabase:         {"✓" if SUPABASE_URL else "✗"}
╚══════════════════════════════════════════════════════════════╝
""")


if __name__ == "__main__":
    print_config()