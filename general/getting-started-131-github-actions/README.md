# GETTING STARTED 131 GITHUB ACTIONS

> **Your complete guide to implementing Issue #131**

**Priority**: P2-Medium | **Effort**: 2.5 weeks | **ROI**: 180%

---

## What You're Building

Bui

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started: GitHub Actions CI/CD Pipeline (Issue #131)

**Your complete guide to implementing Issue #131**

**Priority**: P2-Medium | **Effort**: 2.5 weeks | **ROI**: 180%

---

## What You're Building

Build comprehensive GitHub Actions workflows for automated testing, building, and deploying with real-time status checks and PR integration.

**Why It Matters**: Manual testing and deployment is slow and error-prone. Automate the entire pipeline.

**Business Value**: Reduces deployment time from hours to 15 minutes, catches bugs before PR merge, enables confident continuous deployment.

---

## Before You Start (15 minutes)

### 1. Understand GitHub Actions

**Resources**:
- GitHub Actions Docs: https://docs.github.com/en/actions
- Workflows: https://docs.github.com/en/actions/workflow-syntax-for-github-actions

### 2. Check Current Workflows

```bash
ls -la .github/workflows/
cat .github/workflows/*.yml
```

### 3. Understand Project Structure

```bash
# See what needs to be tested/built
ls -la src/
find . -name "pytest.ini" -o -name "setup.py" -o -name "pyproject.toml" | head -5
```

---

## Phase 1: Create Workflow Structure (Days 1-2, ~8 hours)

### Create Branch

```bash
git checkout main
git pull origin main
git checkout -b feat/issue-131-github-actions
```

### Create Workflows Directory

```bash
mkdir -p .github/workflows
touch .github/workflows/test.yml
touch .github/workflows/build.yml
touch .github/workflows/deploy.yml
touch .github/workflows/security.yml
```

---

## Phase 2: Create Test Workflow (Days 3-4, ~12 hours)

### Create Test Workflow

**File**: `.github/workflows/test.yml`

```yaml
name: Test

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  unit-tests:
    runs-on: ubuntu-latest
    timeout-minutes: 30
    strategy:
      matrix:
        python-version: ["3.11", "3.12"]
    steps:
      - uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        wi

*[truncated — see source for full prompt]*