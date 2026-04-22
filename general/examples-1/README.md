# Examples

> Real-world usage patterns for the BNB Chain AI Toolkit, organized by difficulty.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Examples

Real-world usage patterns for the BNB Chain AI Toolkit, organized by difficulty.

> **How to use this page:** Each example lists what you need, shows the code or conversation, and explains what happens. Start with Beginner and work up.

| Difficulty | What It Means |
|:----------:|--------------|
| 🟢 Beginner | No coding needed, or very simple commands |
| 🟡 Intermediate | Some setup required, basic code |
| 🔴 Advanced | Multiple components, scripting, or on-chain operations |

---

## 🟢 Beginner Examples

### Check a BNB Balance (No Code)

**What you need:** BNB Chain MCP server connected to Claude Desktop (see [Getting Started](getting-started.md#your-first-mcp-server))

**How it works:**

> **You:** What's the BNB balance of 0xF977814e90dA44bFA03b6295A0616a897441aceC?
>
> **Claude:** That address holds 1,234,567.89 BNB (approximately $768 million at current prices). This appears to be a Binance cold wallet.

**Behind the scenes:**
```
Your question → Claude → get_balance tool → BSC RPC → Real balance → Claude's answer
```

**What you learned:** Claude didn't guess. It called the MCP server, which queried the actual blockchain, and returned a real number.

---

### Get Today's Crypto Prices

**What you need:** Market Data component

```typescript
import { CoinGecko } from '@nirholas/crypto-market-data';

const prices = await CoinGecko.getPrices(['bitcoin', 'binancecoin', 'ethereum']);
console.log(prices);
// Expected output: { bitcoin: 95000, binancecoin: 620, ethereum: 3200 }
```

**What you learned:** The market data library fetches real-time prices with one function call. No API key needed for basic usage.

### Read the Latest Crypto News

**What you need:** Crypto News API

```bash
# Start the news server
cd market-data/crypto-news && bun start

# Fetch headlines
curl http://localhost:3000/api/news/latest | jq '.[0:5] | .[].title'
```

**Expected output:** A list of 5 recent crypto headlines.

---

### Check Market Sentiment (No Code)

**What y

*[truncated — see source for full prompt]*