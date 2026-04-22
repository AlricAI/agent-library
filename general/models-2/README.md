# MODELS

> Understanding model parameters helps you fine-tune agent behavior for optimal results.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Model Parameters Guide

Understanding model parameters helps you fine-tune agent behavior for optimal results.

## Core Parameters

### Temperature (0.0 - 2.0)

Controls randomness in responses.

**Low (0.0 - 0.3)**

- Deterministic, consistent output
- Same input → same output
- Best for: Code generation, calculations, factual queries

**Medium (0.4 - 0.7)** \[Default]

- Balanced creativity and consistency
- Slight variations in responses
- Best for: General conversation, analysis

**High (0.8 - 2.0)**

- Creative, unpredictable output
- High variation
- Best for: Brainstorming, creative writing

**Examples:**

```
Query: "Explain smart contract reentrancy"

Temperature 0.0:
"Reentrancy occurs when a function calls an external contract..."
[Same answer every time]

Temperature 0.7:
"Reentrancy is a vulnerability where..."
[Slight variations in phrasing]

Temperature 1.5:
"Picture this: your smart contract is like a bank vault..."
[Creative analogies, different approaches]
```

### Top P (0.0 - 1.0)

Alternative to temperature. Controls diversity by probability threshold.

**How it works:**
Model generates candidate words with probabilities:

- `ethereum` (40%)
- `blockchain` (30%)
- `crypto` (20%)
- `web3` (10%)

**top_p = 0.9**: Include top candidates until 90% cumulative probability
→ Considers: ethereum (40%) + blockchain (30%) + crypto (20%) = 90%

**top_p = 0.5**: Only top 50%
→ Considers: ethereum (40%) only

**Settings:**

- **0.1 - 0.5**: Very focused, conservative
- **0.6 - 0.9**: Balanced diversity \[Default: 0.9]
- **0.95 - 1.0**: Maximum diversity

⚠️ **Don't adjust both temperature AND top_p** - use one or the other.

### Presence Penalty (-2.0 to 2.0)

Penalizes words that already appeared, reducing repetition.

**Negative (-2.0 to -0.1)**

- Encourages repetition
- Reinforces key terms
- Good for: Technical documentation

**Zero (0.0)** \[Default]

- Natural repetition
- Balanced

**Positive (0.1 to 2.0)**

- Discourages repetition
- Forces vocabu

*[truncated — see source for full prompt]*