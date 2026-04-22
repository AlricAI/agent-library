# End To End Data Collection Plan

> ## Repo implementation notes (this repo)

This plan is written to be tool- and storage-agnostic. In this repo, we implement it using a **contract-firs

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Data Collection Plan

## Repo implementation notes (this repo)

This plan is written to be tool- and storage-agnostic. In this repo, we implement it using a **contract-first** layout and **tracked provenance manifests**:

- Canonical definitions: `docs/protocol.md`, `contracts/`, `registry/`
- Raw snapshots (append-only; not committed): `data/raw/<source>/<YYYY-MM-DD>/...`
- Raw provenance (tracked): `data/raw_manifest/<source>_<YYYY-MM-DD>.json` (generated via `python scripts/make_raw_manifest.py ...`)
- Processed artifacts (rebuildable; not committed): `data/processed/<source>/...`
- Processed provenance (tracked): `data/processed_manifest/<name>_<YYYY-MM-DD>.json`
- Golden samples (tracked): `data/samples/...`
- Human-facing outputs (tracked when appropriate): `reports/validation/`, `reports/status/`, `reports/figures/`, `reports/tables/`

When this document mentions `data/reference/`, `data/normalized/`, `data/analysis_ready/`, `data/qa/`, or `data/manifests/`, treat them as conceptual buckets and map them to the repo paths above.

## Phase 0 — Project initialization, protocol lock, and data dictionary

### 1. Phase name and objectives

**Phase 0: Initialization + Protocol Lock**

* Set up the repo, environment, secrets handling, and immutable snapshot conventions.
* Freeze: rollup inclusion rules, STR definition, units, and regime split boundary.
* Produce the authoritative data dictionary and table schemas used by later phases.

### 2. Data requirements

* Protocol metadata:

  * **Dencun activation boundary:** March 13, 2024 13:55 UTC (epoch 269568).
* Rollup universe seed list (initial “candidate rollups”):

  * From growthepie origins list (via master.json).
  * From L2BEAT “rollups” list (manual/derived from site, for cross-check).
* Technical definitions:

  * STR numerator = rollup L1 costs (rent paid).
  * STR denominator = rollup user fees on L2.

### 3. Primary source with detailed collection instructions

**Primary:** growthepie `master.json` (orig

*[truncated — see source for full prompt]*