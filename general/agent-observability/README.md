# Agent Observability

> > If you can't see what your agent did, you can't fix what it does wrong.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Observability

> If you can't see what your agent did, you can't fix what it does wrong.

## The Problem

AI coding agents produce outputs that look correct but fail in subtle ways:
- Hallucinated function names that pass review but fail at runtime
- Tool call sequences that work once but regress under different inputs
- Prompt changes that improve one case but silently degrade another

Standard logging captures commands, not reasoning. You need traces — the full
chain from user input through every tool call to final output.

## The Pattern

Observability for agents has three layers:

| Layer | Answers | When it fires |
|-------|---------|---------------|
| **Tracing** | What did the agent do, step by step? | Every session |
| **Evaluation** | Did the output meet quality criteria? | On key outputs |
| **Regression testing** | Did a change break past behavior? | Before shipping |

Tracing is cheap and should run always. Evaluation and regression testing target
the outputs that matter — not every Bash call, but every generated feature or
answered question.

## Tracing with lmnr

[lmnr](https://github.com/lmnr-ai/lmnr) instruments agent runs and stores traces
you can query, replay, and annotate.

**Install:**
```bash
# macOS — system Python is externally managed (PEP 668); use pipx
pipx install lmnr          # CLI: ~/.local/bin/lmnr

# Ubuntu/Linux
pip3 install lmnr --break-system-packages
```

**Instrument a Python agent:**
```python
from lmnr import observe, Laminar

Laminar.initialize(project_api_key="<LMNR_API_KEY>")

@observe()
def generate_component(prompt: str) -> str:
    # Any LLM or tool calls made here are auto-traced
    result = call_llm(prompt)
    return result
```

**What gets captured per trace:**
- Input/output for every LLM call
- Tool invocations and their results
- Latency per step
- Token usage

**Querying traces:**
```bash
# View recent runs
lmnr traces list --limit 20

# Filter by label or score
lmnr traces list --label "needs-review"
``

*[truncated — see source for full prompt]*