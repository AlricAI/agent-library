# Initialization And Usage

> This guide explains how to initialize PineTS and run indicators or strategies with detailed documentation of all available options and return values.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Initialization and Usage

This guide explains how to initialize PineTS and run indicators or strategies with detailed documentation of all available options and return values.

## Table of Contents

-   [Installation](#installation)
-   [PineTS Constructor](#pinets-constructor)
-   [Initialization Options](#initialization-options)
-   [The run() Method](#the-run-method)
-   [Context Object](#context-object)
-   [Return Values](#return-values)
-   [Complete Examples](#complete-examples)

---

## Installation

\`\`\`bash
npm install pinets
\`\`\`

---

## PineTS Constructor

The `PineTS` class is the main entry point for working with indicators and strategies.

### Syntax

\`\`\`typescript
const pineTS = new PineTS(
    source: IProvider | any[],
    tickerId?: string,
    timeframe?: string,
    limit?: number,
    sDate?: number,
    eDate?: number
);
\`\`\`

### Parameters

| Parameter   | Type                 | Required | Description                                                                          |
| ----------- | -------------------- | -------- | ------------------------------------------------------------------------------------ |
| `source`    | `IProvider \| any[]` | Yes      | Either a data provider instance (e.g., `Provider.Binance`) or an array of OHLCV data |
| `tickerId`  | `string`             | No\*     | The trading pair symbol (e.g., `'BTCUSDT'`). Required when using a provider          |
| `timeframe` | `string`             | No\*     | The timeframe/interval for the data. Required when using a provider                  |
| `limit`     | `number`             | No       | Maximum number of candles to fetch (default: provider-specific, max 5000)            |
| `sDate`     | `number`             | No       | Start date in milliseconds timestamp. Used for date range queries                    |
| `eDate`     | `number`             | No       | End date in milliseconds timestamp. Used for date range queries                      |

\* Required w

*[truncated — see source for full prompt]*