# TOKEN BUDGET

> The token budget system controls how many tokens of learned behavior content are injected into agent system prompts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Token Budget System

The token budget system controls how many tokens of learned behavior content are injected into agent system prompts. It ensures floop stays within LLM context limits while preserving the most important behaviors.

## How Tiering Works

Every behavior is assigned one of four **injection tiers** based on its activation level:

| Tier | Activation Threshold | Content |
|------|---------------------|---------|
| **Full** | >= 0.7 | Complete canonical content |
| **Summary** | >= 0.3 | One-line summary (or truncated canonical) |
| **Name Only** | >= 0.1 | `` `name` [kind] #tags `` |
| **Omitted** | < 0.1 | Not included |

Constraints receive special protection: they are never demoted below **Summary** tier, regardless of activation level. This ensures safety-critical behaviors remain visible.

## Budget Demotion

When the total token cost of all tiered behaviors exceeds the budget:

1. Sort behaviors by activation (ascending)
2. Demote the lowest-activation behavior one tier (Full -> Summary -> Name Only -> Omitted)
3. Recalculate total tokens
4. Repeat until within budget

Constraints are skipped during demotion (they stay at their assigned tier or the constraint minimum tier, whichever is higher).

## Configuration

Configure token budgets in `~/.floop/config.yaml`:

```yaml
token_budget:
  # Budget for MCP resource handlers and CLI default (init, upgrade, prompt)
  default: 2000

  # Budget for hook-triggered activate calls (dynamic context injection)
  dynamic_context: 500
```

### Environment Variable Overrides

| Variable | Overrides | Example |
|----------|-----------|---------|
| `FLOOP_TOKEN_BUDGET` | `token_budget.default` | `FLOOP_TOKEN_BUDGET=3000` |
| `FLOOP_TOKEN_BUDGET_DYNAMIC` | `token_budget.dynamic_context` | `FLOOP_TOKEN_BUDGET_DYNAMIC=800` |

Environment variables take precedence over config file values.

## CLI Flags

The `--token-budget` flag is available on several commands and always overrides both config file and environmen

*[truncated — see source for full prompt]*