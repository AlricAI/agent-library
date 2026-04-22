# QUICK START CONTRIBUTORS

> **Goal**: Get you from zero to first contribution in 15 minutes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Start for Enhancement Contributors

**Goal**: Get you from zero to first contribution in 15 minutes.

## Prerequisites (5 minutes)

```bash
# 1. Clone the repository
git clone https://github.com/rysweet/AzureHayMaker.git
cd AzureHayMaker

# 2. Install dependencies
uv sync --all-extras

# 3. Run tests to verify setup
pytest tests/unit -x
```

## Pick Your Enhancement (2 minutes)

**View available enhancements:**
- [Enhancement Roadmap](ENHANCEMENT_ROADMAP.md) - Full strategic overview
- [Quick Reference Card](ENHANCEMENT_QUICK_REFERENCE.md) - One-page summary
- [GitHub Issues](https://github.com/rysweet/AzureHayMaker/issues?q=is%3Aissue+is%3Aopen+label%3Aenhancement) - All issues

**Priority levels:**
- **P0-Critical** (Start here!) - SIEM Export (#124), Windows VM Security (#125)
- **P1-High** - Multi-Tenant (#126), Tracing (#127), Cost Enforcement (#128), Circuit Breakers (#129)
- **P2-Medium** - Local Dev (#130), GitHub Actions (#131), Dashboard, Testing

**Choose based on:**
1. Your skillset (security, infrastructure, frontend, testing)
2. Time available (Low=1 week, Medium=2-3 weeks, High=4+ weeks)
3. Dependencies (check if any PRs need to merge first)

## Read the Spec (3 minutes)

**All specs are in** `specs/` **directory:**

```bash
# Example: Reading SIEM export spec
cat specs/SIEM_TELEMETRY_EXPORT.md

# Look for these sections:
# - Requirements (what needs to be built)
# - Scope (detailed breakdown)
# - Testing Strategy (how to verify)
# - Success Criteria (definition of done)
```

**Tip**: Specs include code examples and file locations!

## Create Your Branch (1 minute)

```bash
# Create feature branch from main
git checkout main
git pull origin main
git checkout -b feat/issue-XXX-brief-description

# Example:
git checkout -b feat/issue-124-siem-export
```

## Implement & Test (Your Time)

**Follow TDD (Test-Driven Development):**

```bash
# 1. Write failing tests first
# Example: tests/unit/test_siem_export.py

# 2. Run tests (should fail)
pytest 

*[truncated — see source for full prompt]*