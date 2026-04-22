# Release

> Create a release branch and PR to main with auto-extracted changes from staging

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping create a production release. Your task is to create a release branch from the development branch, bump the version, extract changes, and create a comprehensive release PR to the production branch.

## Step 1: Load Configuration

Check for configuration:

```bash
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
workflow:
  type: staging # staging | tag-based | direct
  developmentBranch: staging
  productionBranch: main
branches:
  release: "release/{version}"
versioning:
  file: auto # auto | package.json | pyproject.toml | VERSION | Cargo.toml
release:
  watchFiles:
    openapi: docs/openapi.json
    migrations: prisma/migrations/**/migration.sql
    schema: prisma/schema.prisma
  generateChangelog: true
```

**Default Values:**

```yaml
workflow:
  developmentBranch: staging
  productionBranch: main
branches:
  release: "release/{version}"
versioning:
  file: auto
```

## Step 2: Verify Current State

Check that you're on the development branch and up-to-date:

```bash
# Get configured branches
DEV_BRANCH=$(config.workflow.developmentBranch || "staging")
PROD_BRANCH=$(config.workflow.productionBranch || "main")

# Check current branch
CURRENT=$(git branch --show-current)
echo "Current branch: $CURRENT"
echo "Expected: $DEV_BRANCH"

# Fetch latest
git fetch origin

# Check if up-to-date
git status
```

**Validation:**

- If not on development branch:
  ```
  You must be on {DEV_BRANCH} branch to create a release.
  Run: git checkout {DEV_BRANCH} && git pull
  ```
- If behind remote:
  ```
  Your {DEV_BRANCH} branch is behind origin.
  Run: git pull origin {DEV_BRANCH}
  ```
- If there are uncommitted changes:
  ```
  You have uncommitted changes. Commit or stash them first.
  ```

## Step 3: Detect Version File

Auto-detect or use configured version file:

```bash
# Check for version files in order of priority
if [ -f "package.json" ]; then
  VERSION_FILE="packag

*[truncated — see source for full prompt]*