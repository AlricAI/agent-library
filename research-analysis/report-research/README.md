# report-research

> Write a complete Numerai experiment report in experiment.md (abstract, methods, results tables, decisions, next steps) and generate/link the standard show_experiment plot(s). Use after running any Numerai research experiments, or when a user asks for a “full report”, “write up”, “experiment.md update”, or “generate the standard plot”.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Report Research

## Overview

This skill turns an experiment run into a durable write-up: a full `experiment.md` plus the standard `show_experiment` plot(s) linked from the report.

## Workflow (do all steps)

### 1) Locate the experiment folder

Use the folder that contains:
- `configs/` (the configs you ran)
- `results/` (JSON metrics output)
- `predictions/` (OOF parquet output)
- `experiment.md` (the report you will write/update)

### 2) Inventory what was actually run

- List configs that exist.
- Determine which ones were executed by checking for matching `results/*.json` and `predictions/*.parquet`.
- Identify the “best” model(s) using `bmc_mean` and `bmc_last_200_eras.mean` (primary), with `corr_mean` as a sanity check.
- If experiments were run in rounds, summarize **each round’s intent** (what changed) and whether it improved the current best.

### 3) Extract metrics for the report

For each run you report, include at least:
- `corr_mean`
- `bmc_mean`
- `bmc_last_200_eras.mean`
- `avg_corr_with_benchmark` (from the BMC summary)

Prefer a single markdown table with one row per model.

### 4) Write a full report in experiment.md

Update/create `experiment.md` with these sections (keep it crisp but complete):
- **Title + Date**
- **Abstract** (what was tested + headline result)
- **Hypothesis / Motivation** (why this should help BMC)
- **Method** (data split, CV, feature set, model type/hparams, any transforms)
- **Experiments run** (one subsection per config that actually ran; include output artifacts)
- **Results** (the metrics table; mention best run + trade-offs)
- **Standard plot** (embed the PNG and include the generating command)
- **Decisions made** (what you chose and why; e.g., per-era vs global, feature set choice, sweep choices)
- **Stopping rationale** (why you stopped iterating; e.g., plateau after N rounds, confirmatory scale step, diminishing returns)
- **Findings** (what worked / didn’t; interpret the plot)
- **Next experiments** (2–5 concr

*[truncated — see source for full prompt]*