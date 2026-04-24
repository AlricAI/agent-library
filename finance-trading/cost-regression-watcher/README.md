## Overview
The Cost Regression Watcher is a critical, automated financial monitoring agent designed to prevent unmanaged cost overruns within operational workflows. It operates daily by analyzing the last 24 hours of cost events and comparing key metrics against a rolling seven-day baseline.

Its primary function is not to fix bugs, but to act as an early warning system, flagging any metric that deviates significantly (e.g., >20% or >50%) from established spending patterns so that leadership can intervene before costs compound.

## Capabilities
*   **Daily Cost Aggregation:** Pulls and processes the last 24 hours of cost data from live SQL sources.
*   **Baseline Comparison:** Computes key metrics and compares them against a dynamically maintained 7-day rolling average baseline.
*   **Automated Alerting:** Files high-priority Forge issues when specified metrics exceed predefined regression thresholds (>20% or >50%).
*   **Data Integrity Checks:** Performs data quality gates, ensuring at least 80% of records have non-null cost data before proceeding with analysis.
*   **Reporting & Documentation:** Updates the rolling baseline JSON and posts a comprehensive daily digest summarizing performance to the designated issue tracker.

## Example Use Cases
*   **Detecting Unexpected Spikes:** If an agent suddenly starts using significantly more API calls or compute time than usual, this watcher will flag it immediately, alerting the COO before budget overruns occur.
*   **Post-Deployment Validation:** After deploying a new model or routine, running this agent helps validate that the associated cost increase is within expected parameters.
*   **Cost Discipline Enforcement:** It provides objective, data-backed evidence of spending drift, forcing accountability and immediate investigation into the root cause (agent, model, or routine).

**Note:** This agent reports regressions with a clear hypothesis but does not implement fixes; it escalates findings to human decision-makers.