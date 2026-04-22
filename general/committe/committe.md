---
name: Committe
description: ---
## ICP Qualification (Legacy On-Prem)

| Signal | Target |
|--------|--------|
| Company size | 500+ employees |
| Tech stack | SharePoint 2
model: claude-sonnet-4-5
---
# Committe Targeting
---
## ICP Qualification (Legacy On-Prem)

| Signal | Target |
|--------|--------|
| Company size | 500+ employees |
| Tech stack | SharePoint 2016/2019, Exchange on-prem, file servers |
| Industry | Government, Healthcare, Financial Services, Manufacturing |
| Trigger | End-of-support dates, audit finding, talent gap, M&A |

---


## Buying Committee Map

| Role | Title Examples | Influence | Primary Concern | Message Angle |
|------|----------------|-----------|-----------------|---------------|
| **Champion** | IT Director, Dir. of Infrastructure, SharePoint Admin | High — drives initiative | Ownership, drift, maintenance burden, talent retention |  =ownership + cadence |
| **Influencer** | VP IT, CISO, Finance Director | Medium–High | Cost of ownership, security posture, compliance | TCO, risk reduction, compliance |
| **Decision Maker** | CIO, CTO | Budget, final sign-off | Strategic alignment, vendor risk, change management | Outcomes, proof, referenceability |
| **Stakeholder** | Business unit leaders, HR, Legal | Medium — can block | Reliability, user experience, continuity | "No surprises" — phased rollout, training |

---


## Messaging by Role (Table)

| Role | Titles | Pains | Email / Note Draft |
|---|---|---|---|
| Champion | IT Director; Director of Infrastructure; Senior SharePoint/Exchange Admin | EOL platforms (SP 2016/2019, Exchange); ownership drift (orphaned sites, permission sprawl); maintenance (patching/upgrades/backup); talent gap | **Email:** “[Name], we work with [similar company type] still running SharePoint 2016/2019 or Exchange on-prem. The common pattern is ownership drift + patch cycles turning into downtime risk. If useful, we can run a quick assessment to map what to clean up vs migrate first, and outline a phased plan to M365/EXO.” |
| Influencer (Finance / VP IT) | Finance Director; VP IT | On-prem TCO (hardware, licenses, maintenance, headcount) | **Email:** “[Name], when SharePoint/Exchange stay on-prem past their prime, TCO isn’t just hardware—it’s patch cycles, downtime risk, and admin time. We help teams quantify that cost and translate it into a phased migration plan so spend stays controlled. Want the simple TCO model we use for 500+ employee environments?” |
| Influencer (Security) | CISO; Security Director | Compliance exposure; audit findings; breach risk from legacy platforms | **Email:** “[Name], we’re seeing legacy SharePoint/Exchange show up as repeat audit findings—patch gaps, inconsistent access controls, and limited visibility for retention/eDiscovery. Our approach is to modernize while tightening controls in parallel (identity, conditional access, DLP/labels, logging) so security improves during the migration. If you’re under audit pressure, I can share the control checklist we use.” |
| Decision Maker | CIO; CTO | Strategic fit; vendor risk; change management; exec/board reporting | **Email:** “[Name], [Champion] mentioned you’re evaluating options for SharePoint/Exchange modernization. We’ve run [X] similar migrations for [industry/size], with a phased rollout that protects continuity and reduces risk. Happy to share a short reference from a comparable org and walk through timeline + risk controls if that helps for executive reporting.” |
| Stakeholder | HR; Legal; Department heads | “Will my stuff still work?” “Will we lose access?” | **Internal note (Champion can forward):** “We’re bringing in a partner to review our SharePoint/file share structure before we modernize. Goal: clearer ownership, less drift, and a smoother move to M365. No disruption to day-to-day—we’ll coordinate access and timing, and provide training/communications ahead of any change.” |



### 0.4 Who

| Role / Title Mentioned | Typical Asks (Observed) | Best Entry Wedge (Low-friction offer) |
|---|---|---|
| IT Manager / IT Director | Exchange migration, SharePoint setup, M365 optimization, helpdesk outsourcing | **M365 / SharePoint Health Check** (permissions, drift, security, roadmap) |
| Director of IT | SharePoint, M365, AI strategy | **Copilot Readiness + Governance** (SPO/Teams/OneDrive + labels/DLP) |
| Director of Enterprise Applications | InfoPath conversion, SharePoint | **App modernization assessment** (InfoPath → Power Apps + workflow plan) |
| CTO | Google → M365 migration, tenant consolidation | **Tenant consolidation plan** (phased cutover + identity/security checklist) |
| CIO / C-level | AI strategy, governance, security | **AI roadmap + guardrails** (use cases + risk controls + adoption plan) |
| Director of BI | Power BI dashboards, data architecture | **Dashboard + data foundation blueprint** (sources, model, governance) |
| Program Manager | Dashboards, data extraction, BI | **Fast dashboard pilot** (single function dashboard in 2–3 weeks) |
| Marketing Manager | HubSpot setup, workflows, attribution | **HubSpot cleanup + workflow sprint** (dedup + lifecycle + reporting) |
| Director of Operations | BPO, customer service outsourcing | **Service desk / CX assessment** (coverage, SLAs, transition plan) |
| HR / Ops Manager | Onboarding automation, Power Automate | **Onboarding automation sprint** (Power Automate + approvals) |

---

### 0.5 What
| Category | Top Needs (Grouped) | Example Work (What You Actually Deliver) | Common Integrations / Systems Mentioned |
|---|---|---|---|
| **SharePoint / Intranet** | Intranet build/upgrade; Migrations; Governance/structure; Document management; Integrations | Classic→modern refresh, IA + permissions cleanup, file server/Box/Google Drive/on-prem→SPO migration, metadata/search/DMS design, site lifecycle + ownership model | Salesforce, Deltek, MS Project |
| **Power BI & Analytics** | Dashboards; BI migrations; Data architecture; Ongoing support | Finance/ops/clinical dashboards, Tableau/SAP BO/SSRS→Power BI migration, warehouse + ETL + connectors, training + governance + managed support | Tableau, SAP BusinessObjects, SSRS |
| **Microsoft 365** | Migrations; Optimization; Exchange migrations | Google Workspace→M365, tenant-to-tenant moves/mergers, security + governance hardening, Exchange (Intermedia/on-prem)→Exchange Online | Google Workspace, Intermedia, Exchange on-prem |
| **Dynamics 365 / Business Central** | Implementation; Migration; Setup/training | D365 Sales/CS/F&O implementations, GP→BC and NetSuite→BC migrations, cleanup + configuration + enablement | GP, NetSuite |
| **HubSpot** | Setup/config; Cleanup; Migration | Workflow automation, Stripe + app integrations, inherited portal cleanup/dedup, Salesforce→HubSpot migration | Stripe, Salesforce |
| **AI / Copilot** | Strategy/roadmap; Implementation; Training | Use-case prioritization, Copilot/ChatGPT rollout + guardrails, internal AI tool enablement, exec/leadership training | Copilot, ChatGPT |
| **BPO / Helpdesk / Call Center** | IT helpdesk; Customer service; Specialized ops | L1/L2 + 24/7 coverage, NOC/SOC support, phone/email/chat service, claims intake/registration support | NOC/SOC |
| **Power Platform** | Workflows; Forms/approvals; Apps | Approval flows + automation, Nintex→Power Apps conversions, lightweight internal apps for teams, Power Pages as needed | Nintex, Power Apps/Automate/Pages |
| **Other** | CRM; Compliance; Sitefinity; NetSuite | Salesforce implementation / Dynamics Sales setup, Purview + labels/DLP, CMMC/HIPAA controls, Sitefinity migration/maintenance, NetSuite integrations | Purview, Sitefinity, NetSuite |

---