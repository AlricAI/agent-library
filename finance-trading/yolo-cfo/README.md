## Overview
This agent acts as a highly critical Chief Financial Officer (CFO), dedicated to tracking every dollar spent and earned. It moves beyond optimistic projections, grounding all analysis in hard data from AWS Cost Explorer, external revenue sources (like Shopify GMV), and operational metrics.

Its core mandate is to provide an unvarnished financial picture: determining the true burn rate, flagging potential revenue risks due to expired credentials, and ruthlessly identifying wasteful cloud spending.

## Capabilities
*   **Burn Rate Calculation:** Accurately calculates current monthly run rates and forecasts end-of-month expenditure using AWS Cost Explorer data.
*   **Cost Anomaly Detection:** Scans AWS services to identify any resource costing over a specified threshold ($5/month) that may be unnecessary or oversized.
*   **Resource Waste Identification:** Checks for idle EC2 instances, unattached EBS volumes, and old snapshots to recommend immediate cost-saving actions.
*   **Holistic Financial View:** Integrates internal AWS costs with external project revenue (e.g., Shopify GMV) to give a complete picture of financial health.
*   **Risk Flagging:** Specifically alerts on external projects where credentials have expired, posing an immediate revenue risk.

## Example Use Cases
*   **Quarterly Budget Review:** Run this agent against the last quarter's AWS logs and Shopify data to determine if the current spending trajectory is sustainable given projected Q3 revenue.
*   **Cost Optimization Audit:** Feed it raw AWS cost reports and ask, "Which services are consuming resources without clear ROI?" to generate a prioritized list of rightsizing opportunities.
*   **Pre-Investment Due Diligence:** Provide all operational data for a potential acquisition target. The agent will immediately flag any revenue streams that appear dormant or linked to expired credentials.