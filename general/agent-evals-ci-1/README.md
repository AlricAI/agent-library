# Agent Evals Ci

> > **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
> **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR. Contribute to [ai-dev-toolkit-pt-br](https://github.com/LucasSantana-Dev/ai-dev-toolkit-pt-br/issues).

# Agent Evaluation as CI/CD Gate

Unit tests catch deterministic bugs. Evals catch stochastic failures. A coding agent that refactors 95% of SQL queries correctly but corrupts 5% isn't "95% good" — it's broken. Evals-as-CI makes agent reliability measurable: fail the PR if success rate drops below threshold.

> _Pattern informed by LangSmith's eval workflows, which gate production deploys on held-out test sets; also observed in production at Vercel (AI-assisted refactoring), Stripe (fraud-detection agents), and early adoption in anthropic/prompt-library._

## Why evals, not unit tests

Unit tests validate deterministic code paths. Agent evals validate stochastic behavior across varied inputs.

| Unit test | Agent eval |
|---|---|
| Input: `greet("Alice")` → Output: `"Hello, Alice"` (deterministic) | Input: `"Refactor this SQL to use window functions"` → Output: varies (stochastic) |
| Cost: negligible | Cost: 1-50 tokens per eval case |
| Speed: <1ms | Speed: 1-5s per case (LLM latency) |
| Suitable for: Business logic, data transform | Suitable for: LLM quality, robustness, edge cases |

An eval that passes 100% of the time is worthless (overfit). An eval that captures real failure modes (bad refactors, missed requirements, hallucination) is gold.

## Eval dataset curation

Create a dataset of diverse, real-world test cases:

```python
EVAL_DATASET = [
    {
        "task": "Refactor SQL to use window functions",
        "input": "SELECT user_id, count(*) FROM orders GROUP BY user_id",
        "expected_criteria": [
            "contains ROW_NUMBER() or RANK()",
            "no SELECT COUNT(*) inside aggregation",
            "preserves original logic",
        ],
        "success_threshold": 2/3,  # 2 of 3 criteria must pass
    },
    {
        "task": "Detect prompt injection",
     

*[truncated — see source for full prompt]*