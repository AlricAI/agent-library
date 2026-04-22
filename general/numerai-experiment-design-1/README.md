# numerai-experiment-design

> Design and manage Numerai experiments in this repo for any model idea.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Numerai Experiment Design
Use this workflow to plan, run, and report Numerai experiments for any model idea.

Note: run commands from `numerai/` (so `agents` is importable), or from repo root with `PYTHONPATH=numerai`.

## Persistence expectation (required)

This skill is *not* complete after a single promising run. You must run experiments in **rounds** (typically **4–5 configs per round**), synthesize results, and decide what to try next. Only finalize when you reach a plateau and additional rounds stop improving the primary metric.

## Planning checklist (answer before running)
- State the model idea and novelty.
- Choose the initial baseline and feature set. Default to `deep_lgbm_ender20_baseline` (feature_set=all) unless the user explicitly requests the small baseline; keep experiments' feature_set aligned with the chosen baseline.
- Decide the primary metric (`bmc_mean` and `bmc_last_200_eras`) where BMC = Benchmark Model Contribution vs official `v52_lgbm_ender20`.
- Decide which parameter dimensions to explore based on the core idea (targets, model hyperparameters, ensemble weights, data settings).
- Or decide that only a minimal round is needed because the change is tiny — but still run multiple variants unless the user explicitly requested exactly one run.

## Handling ambiguity (fast disambiguation)
If the user's request is unclear or underspecified:
1) List 2–4 plausible interpretations (keep them meaningfully different).
2) Implement **quick scout runs** for each interpretation (downsampled data, conservative compute).
3) Compare `bmc_mean` and `bmc_last_200_eras`.
4) Use the best-BMC interpretation going forward, and document the choice + rationale in `experiment.md`.

## Workflow 
Core loop (repeat for each experiment round):
1) If the model type is new, implement it with the numerai-model-implementation skill.
2) Create/update **4–5 configs** for the current round (one base + single-variable variants).
3) Run training for each config via `PYTHONPAT

*[truncated — see source for full prompt]*