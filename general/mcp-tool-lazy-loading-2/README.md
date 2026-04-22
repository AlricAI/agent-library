# Mcp Tool Lazy Loading

> > **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
> **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR. Contribute to [ai-dev-toolkit-pt-br](https://github.com/LucasSantana-Dev/ai-dev-toolkit-pt-br/issues).

# MCP Tool Lazy-Loading

Eager loading of MCP tool schemas burns context. Claude Code manages 50+ MCP tools across Anthropic plugins, GitHub, Vercel, and custom integrations. Loading all schemas upfront (even filtered to `name` and `description`) consumes 15-25K tokens. For agentic flows with 1-5 target tools per request, lazy schema retrieval trades context efficiency for discovery latency.

> _Pattern informed by Claude Code's ToolSearch implementation, which queries MCP registries by keyword and retrieves only matched tool schemas on demand._

## When to lazy-load

**Lazy-load required**: You integrate 30+ MCP tools or tool instances across multiple servers. The union of all schemas exceeds your context budget.

**Eager-load is fine**: You have <10 tools total, or context budget is unconstrained.

**Hybrid**: Eager-load tool metadata (name + 1-line description), lazy-load full schemas + parameter details.

Empirically, agentic loops that lazy-load save 40-60% context vs. eager all-in-one approach, at the cost of ~500ms per ToolSearch query.

## Schema overload: the problem

```python
# Eager loading: all schemas loaded upfront
mcp_tools = [
  {"name": "web_search", "schema": {...1200 tokens...}},
  {"name": "calculator", "schema": {...800 tokens...}},
  # ... 48 more tools
]
# Total: ~50K tokens, 5% of a 1M-token context window alone
```

Worse: if you're doing few-shot examples (CoT, chain-of-thought) or multi-turn agentic loops, you're re-sending these schemas every turn. Cumulative waste grows fast.

## Lazy-loading approach

1. **Load tool registry metadata only**: name, one-line description, tags.
   ```json
   {"name": "web_search", "description": "Search the web", "tags": ["search", "web"]}
   ```

2. **User query arrives.** Embed it or use keyword matching to find relevant too

*[truncated — see source for full prompt]*