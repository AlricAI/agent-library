# MASTER AGENT PROMPTS GUIDE

> **Date: April 18, 2026**  
**Version: 1.0**

You now have **9 complete agent YAML configurations** + **master prompts** ready to integrate into your V

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🎯 Master Agent Prompts – Integration & Usage Guide

**Date: April 18, 2026**  
**Version: 1.0**

You now have **9 complete agent YAML configurations** + **master prompts** ready to integrate into your VorstersNV orchestrator framework.

---

## 📦 What You Have

### Test & QA Agents (6)
1. **test_orchestrator_agent.yml** (LEAD)
   - QA Orchestrator — delegates to 6 specialists
   - Produces complete test packs (BDD, Xray, automation, data, security, regression)

2. **domain_validation_agent.yml** (SUB-AGENT)
   - Extracts payroll/HR rules as atomic validations
   - Flags edge cases and ambiguities

3. **test_design_agent.yml** (SUB-AGENT)
   - Converts rules → BDD/Gherkin + Xray tests
   - Maps to JIRA for traceability

4. **automation_agent.yml** (SUB-AGENT)
   - Suggests Cypress/API automation candidates
   - Provides code skeletons

5. **test_data_designer_agent.yml** (SUB-AGENT)
   - Creates boundary + combinatorial datasets
   - Designs setup/reset strategies

6. **security_permissions_agent.yml** (SUB-AGENT)
   - Validates RBAC, audit requirements
   - Tests access control & least privilege

7. **regression_selector_agent.yml** (SUB-AGENT)
   - Intelligent regression selection
   - Maps change → impact → test packs

### Implementation & Design Agents (2)
8. **developer_agent.yml** (SPECIALIST)
   - Translates specs into code-level tasks
   - Produces API contracts, validation pseudocode, error messages

9. **architect_agent.yml** (SPECIALIST)
   - Designs robust architecture with compliance
   - Security, audit, data history, scalability

---

## 🚀 How to Use These

### Option 1: Use Test Orchestrator for a Feature

```bash
# Input to test_orchestrator_agent:
SPEC: "Feature: Allow payroll managers to bulk re-trigger 
       e-Gov 3.0 declarations with amended data"

CONTEXT: domain=flexi_at_work, 
         compliance=GDPR+Belgian_payroll_law,
         assume_missing=true

OUTPUT: Complete test pack (BDD + Xray + Cypress skeletons + 
        test data + RBA

*[truncated — see source for full prompt]*