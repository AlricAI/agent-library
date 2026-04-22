# Program Template

> Replace this template with your own research strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# [Project Name] AutoResearch

Replace this template with your own research strategy. Be specific — the agent reads
this document to decide what to change each iteration.

## Goal

**Maximise / minimise `<metric>` on `<evaluation set>`.**

Current baseline: **`<metric>` = `<value>`**

Describe what the metric measures and why it matters for your task.

## What you CAN modify

List the editable files defined in `research.env` and what's fair game inside each:

**`model.py`**:
- Hidden layer sizes (currently X) — try 2×, 4×
- Number of layers (currently N) — try N+1, N+2
- Dropout rate (currently X) — try 0.1, 0.3, 0.5
- Activation functions — try ReLU, GELU, SiLU

**`train.py`** — training hyperparameters only:
- Learning rate (currently X) — try X/3, X/10
- LR scheduler — try cosine warmup+cooldown, step decay
- Batch size (currently N) — try N/2, N*2
- Regularisation — try weight decay, label smoothing

## What you CANNOT modify

- **`data/`** — dataset is fixed, never regenerated mid-loop
- **Evaluation logic** — the function/script that computes the metric is frozen
- The `--seed` flag — reproducibility is non-negotiable
- Any file not listed above under "What you CAN modify"
- Do NOT install new packages

## Experiment Priorities

Try these in order — ranked by expected impact. Each is a single, targeted change:

1. **[Highest-impact change]** — reason why
2. **[Second change]** — reason why
3. **[Third change]** — reason why
4. **[Architecture change]** — reason why
5. **[LR/optimiser change]** — reason why
6. **Combine #1 + #2** — stack the two best changes
7. **[More radical idea]** — if simpler ideas plateau

Add as many as you can think of. The agent works through them in order and loops back
to combinations after exhausting the list.

## Simplicity Criterion

- Improvement < `MIN_DELTA` (from `research.env`) → discard even if technically positive
- Improvement requires ugly, complex code → probably not worth keeping
- Improvement comes from deleting code →

*[truncated — see source for full prompt]*