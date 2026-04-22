# End To End Research Plan

> ### Core research question

**Is Ethereum L1’s “take rate” on rollup economics rising, stable, or decaying toward ~0 as L2 usage scales?**

This opera

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## RESEARCH OVERVIEW

### Core research question

**Is Ethereum L1’s “take rate” on rollup economics rising, stable, or decaying toward ~0 as L2 usage scales?**

This operationalizes Lyn Alden’s core critique: *utility rails face competition and their revenues trend toward marginal cost*, so coinholders often don’t capture sustained value—even if the rails are useful.

### Research objectives and scope

**Objective 1 (primary):** Quantify and trend-test Ethereum L1’s take rate on L2 user-fee revenue using real data.
**Objective 2 (mechanism):** Decompose the take rate into **(i) burn to all ETH holders** vs **(ii) tip revenue to validators/stakers**, and test whether rollup scaling reliably increases either. ([Ethereum Improvement Proposals][1])
**Objective 3 (regimes):** Identify whether take rate is **regime-dependent** (e.g., “blob fees at minimum for long periods” vs “blob congestion spikes”). ([Galaxy][2])
**Objective 4 (policy):** Quantify how a blob-fee floor/reserve mechanism (e.g., EIP‑7918) would have changed take rate historically (counterfactual).

**Scope boundaries (keep it sharp):**

* Focus on **Ethereum mainnet settlement** and **rollups that post data to Ethereum** (optimistic + ZK rollups).
* Time window: from **Jan 1, 2022 → present** (captures meaningful L2 era; includes EIP‑4844 “Dencun” regime change on **March 13, 2024**). ([Galaxy][2])
* Exclude: token price forecasting, “ETH monetary premium” debates not tied to measurable fee/burn/issuance channels, and non-Ethereum DA (except as a competitive explanation, not as the core measurement).

### Why this research matters

* **Investors:** Separates “Ethereum is used” from “ETH captures value,” directly addressing Alden’s “rails vs value capture” critique.
* **Governance / protocol design:** Provides evidence for or against changes aimed at tightening the link between L2 growth and L1 economics (e.g., EIP‑7918’s reserve price motivation).
* **L2 ecosystem participants:** Makes L2 margin vs L1 re

*[truncated — see source for full prompt]*