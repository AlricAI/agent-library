# Data Dictionary

> This file is the canonical reference for tables/fields/units/keys used in the project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Data Dictionary (contract)

This file is the canonical reference for tables/fields/units/keys used in the project.

## Tables

### daily_rollup_panel

- Purpose: Analysis-ready daily rollup panel used to compute Settlement Take Rate (STR).
- Primary key: (`date_utc`, `rollup_id`)
- Grain: daily × rollup (UTC)
- Row inclusion rule: rows exist **iff** both `l2_fees_eth` and `rent_paid_eth` are present (missingness is represented by omitting the row, not by nulls).
- Source(s):
  - Primary denominator (`l2_fees_eth`): growthepie (ETH-native series)
  - Authoritative numerator (`rent_paid_eth`): on-chain computed rollup costs (see `rollup_costs_daily`)
  - Vendor series (`profit_eth`, `txcount`): growthepie (optional; used for sanity checks / controls)

#### Fields

| Field | Type | Units | Nullable | Description |
|---|---|---|---|---|
| `date_utc` | date | YYYY-MM-DD (UTC) | no | UTC date for daily aggregation |
| `rollup_id` | string | slug | no | Stable rollup identifier (see `registry/rollup_registry_v1.csv`) |
| `l2_fees_eth` | number | ETH | no | Total user fees paid on the rollup for `date_utc` (ETH-native) |
| `rent_paid_eth` | number | ETH | no | Total fees paid by the rollup to Ethereum L1 for settlement/DA/proofs for `date_utc` (ETH-native) |
| `profit_eth` | number | ETH | yes | Vendor-provided profit series; used only for sanity checks (`profit ≈ fees − rent`) |
| `txcount` | integer | count | yes | Transaction count (if provided) |

### daily_rollup_panel_v2

- Purpose: Enriched analysis-ready daily rollup panel (v2) for regime analysis, decomposition, and counterfactuals.
- Primary key: (`date_utc`, `rollup_id`)
- Grain: daily × rollup (UTC)
- Row inclusion rule: rows exist **iff** both `l2_fees_eth` and `rent_paid_eth` are present. Additional enrichment fields may be nullable.
- Source(s):
  - Core STR fields: same as `daily_rollup_panel` (on-chain `rent_paid_eth` + growthepie `l2_fees_eth`)
  - Decomposition fields: on-chain computed rollup decomposi

*[truncated — see source for full prompt]*