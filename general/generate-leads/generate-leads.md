---
name: Generate Leads
description: **Goal:** Reusable system prompts for agents that do **Parse → Find → Interpret → Construct** to (1) pick target accounts and (2) build role-based messaging.
model: claude-sonnet-4-5
---
# Generate Leads

**Goal:** Reusable system prompts for agents that do **Parse → Find → Interpret → Construct** to (1) pick target accounts and (2) build role-based messaging.

**Inputs:**  
- Cloud Migration Targeting System Prompt.md  
- Messaging Prompt System Prompts.md

---

## 1) Prompt List

| Prompt | Use | When you run it |
|---|---|---|
| **Cloud Migration Targeting** | Build + rank a target account list for M365/SharePoint/Exchange/tenant work | “Find companies to target for cloud migration…” |
| **Messaging Motion** | Create outreach by role (Champion/Influencer/Decision/Stakeholders) | “Create messaging motion for [ICP/industry/service]…” |

---

## 2) Targeting Workflow 

## Workflow (Simple)

1. **Prospect**
   - Use: **Company Type Target Matrix / Reference.md**
   - Output: **Company type → Service → Phrase**

2. **Message**
   - Use: **Messaging Framework Summary / Outbound**
   - Output: **Persona → Channel → Offer**

3. **Prioritize**
   - Use: **Open Leads Best to Target / Texas CRM / ATX Leads**
   - Output: **Tier 1–3 by title fit**

4. **Proof**
   - Use: **Case Study Playbook / Case Study Value Prop Mapping**
   - Output: **Pain → Case Study**

5. **Segment**
   - Use: **Vendor Channel / Company Service Title / Analysis Report**
   - Output: **Win rates → best industries/services → channel reality**


### PARSE (turn ICP into filters)
- **Region**
- **Industry** (e.g., Healthcare, Government, Financial Services, Manufacturing, Non-Profit)
- **Size** (employees / revenue threshold)
- **Scope** (Microsoft-adjacent cloud + workplace, not “core ERP only”)

### FIND (build signals + short evidence)
Build an initial universe list (e.g., 200–300 companies) from sources you have (CRM, chamber lists, directories, LinkedIn company search, etc.).  
Then attach **evidence links** for:

**Legacy/on-prem signals (examples)**
- SharePoint Server 2016/2019
- Exchange Server / Hybrid Exchange
- File servers / Windows Server
- VMware
- ADFS / legacy identity
- “On-prem” or “hybrid” language in job posts

**Trigger signals (must be current)**
Keep accounts where you can verify **2+**:
- EOL / upgrade project
- Audit / compliance pressure
- Hiring gap (open roles that suggest backlog)
- M&A / reorg / consolidation

### INTERPRET (apply constraints)
- **Include:** Microsoft workloads (M365, SharePoint, Exchange, tenant consolidation, identity/security, Intune)
- **Exclude:** “SAP RISE-only” or “Oracle-only” migration targets
- **Prefer:** Companies already Microsoft-adjacent (Dynamics/Copilot/Azure signals)

### CONSTRUCT (rank + output)
Score each company **0–3** on:
- **Fit** (industry + size match)
- **Tech** (strength of legacy/on-prem evidence)
- **Trigger** (how current/urgent)
- **Access** (can you find the right titles easily)

Select **Top 30** by total score.

---

## 3) Committee Workflow (Top 30 → Reachable Top 20)

### Committee map (3–6 people / account)
| Role | What you need | Examples |
|---|---|---|
| **Champion** | Runs the work, feels the pain | IT Director, Director of Infrastructure, Sr SharePoint Admin, Exchange Admin |
| **Decision** | Approves vendor + budget | CIO, CTO, VP IT, VP IS |
| **Influencer** | Validates cost/risk | Finance Director/VP Finance **or** CISO/Security Director |
| **Stakeholders** *(optional)* | Affected departments | HR Ops, Legal Ops, Dept heads |

**Minimum viable set per account**
- **Champion + Decision + (Finance OR Security Influencer)**

### Reachability rule
Drop any account where you can’t find:
- **Champion + Decision**

### Final cut
From the reachable set, pick the **best 20**:
- Highest total score
- Clean contact coverage (Champion + Decision + Influencer present)

---

## 4) Messaging Motion Workflow

### PARSE (from whatever data you have)
- Ask/category signals (SharePoint, Power BI, Dynamics, helpdesk, migration)
- Company type (domain hints like .gov / .edu when available)
- Persona (title → Function × Seniority)

### FIND (patterns)
- Title ↔ ask patterns
- Industry ↔ service patterns
- Channel reality (email vs LinkedIn) if you have source data

### INTERPRET (map)
- Ask → service packaging
- Pain language from inputs (urgent, end of life, messy, need help)
- Keep it literal: no “value prop” filler

### CONSTRUCT (deliverables)
- Role-based messaging blocks (Champion, Influencer, Decision; Stakeholders optional)
- Simple cadence (touches + channel)
- Always cite sources for claims when web/data is used

---

## 5) Output Rules (Hard)

- Short bullets, plain English
- No invented facts
- Every “Legacy” and “Trigger” line includes **one link/source**
- Tables over paragraphs

---

## 6) Deliverable Format (what the agent outputs)

| Company | Industry | Employees | Legacy | Trigger | Champion | Decision | Influencer | Notes |
|---|---|---:|---|---|---|---|---|---|
|  |  |  | one line + link | one line + link | Name — Title | Name — Title | Name — Title |  |

---