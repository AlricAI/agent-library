# Scripts

> **Purpose:** Analysis and automation scripts for prospecting data.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scripts — Deep Synthesis

**Purpose:** Analysis and automation scripts for prospecting data. Run from repo root. Each script produces structured output for reports or downstream use.

**Source:** All .py files under scripts/, grep of function definitions, docstrings.

---

## Part 1: Script Inventory and Purpose

| Script | Input | Output | Purpose |
|--------|-------|--------|---------|
| run_analysis.py | Oops.csv | reports/Analysis Report.md | Opportunity segmentation, win rates, segment attractiveness |
| persona_normalization.py | Oops.csv | outbound/Segment Packs | Persona win rates, LinkedIn fit, copy variants |
| deep_parse_inbound.py | Inbound.xlsx | reports/Inbound What They Want.md | Granular Ask, Title×Ask, Industry×Ask, pain language |
| analyze_inbound.py | Inbound.xlsx | reports/Inbound Analysis Report.md | Category distribution, theme frequency |
| company_target_matrix.py | Inbound.xlsx (+ Email) | reports/Company Type Target Matrix.md | Company Type × Ask × Service, service phrases |
| company_service_title_analysis.py | Oops + Inbound + case studies | data/patterns/company_service_title.json | Company × Service × Title patterns |
| analyze_atx_leads.py | Open Leads + Directors lists | reports/ATX Leads Best to Target.md | Austin leads for MW and Marketing |
| run_conversion_teardown.py | URL | Structured checklist | Landing page conversion analysis |
| run_attribution_check.py | URL | Short report | UTM, forms, landing URL check |
| scrape_austin_chamber.py | — | directory.csv, directory.json | Austin Chamber member scrape |
| scrape_affirma_services.py | — | affirma_what_we_do.md | Affirma.com service pages scrape |
| parse_case_studies.py | assets/*.pptx | Case study list | Extract client, service, pains from PPTX |
| parse_all_case_studies.py | assets/ | Full parse | Comprehensive case study extraction |
| organize_assets_by_service.py | assets/ | Service folders | Organize case studies by service |
| organize_other_deeper.py | assets/Other/ 

*[truncated — see source for full prompt]*