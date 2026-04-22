# Sync

> Back-merge main to staging after a release to keep branches synchronized

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping sync the production branch changes back to the development branch. This command should be run AFTER a release has been merged to production and deployed to keep branches aligned.

## Step 1: Load Configuration

Check for configuration:

```bash
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
workflow:
  developmentBranch: staging
  productionBranch: main
branches:
  sync: "sync/main-to-{devBranch}"
versioning:
  file: auto
```

**Default Values:**

```yaml
workflow:
  developmentBranch: staging
  productionBranch: main
branches:
  sync: "sync/main-to-{devBranch}"
```

## Step 2: Verify Current State

Check that you're on the production branch and up-to-date:

```bash
PROD_BRANCH=$(config.workflow.productionBranch || "main")
DEV_BRANCH=$(config.workflow.developmentBranch || "staging")

# Get current branch
CURRENT=$(git branch --show-current)

# Pull latest
git pull origin ${PROD_BRANCH}
```

**Validation:**

- If not on production branch:
  ```
  You should be on {PROD_BRANCH} branch to create a sync PR.
  Run: git checkout {PROD_BRANCH} && git pull
  ```

## Step 3: Get Current Version

Read the version for reference in PR:

```bash
# Auto-detect version file
if [ -f "package.json" ]; then
  VERSION=$(node -p "require('./package.json').version")
elif [ -f "pyproject.toml" ]; then
  VERSION=$(grep -Po '(?<=version = ")[^"]*' pyproject.toml)
elif [ -f "Cargo.toml" ]; then
  VERSION=$(grep -Po '(?<=^version = ")[^"]*' Cargo.toml)
elif [ -f "VERSION" ]; then
  VERSION=$(cat VERSION)
else
  VERSION="unknown"
fi
```

## Step 4: Check What Needs Syncing

Show what commits will be synced:

```bash
git fetch origin ${DEV_BRANCH}
git log origin/${DEV_BRANCH}..origin/${PROD_BRANCH} --oneline --no-merges
```

Display to user:

```
Commits to sync from {PROD_BRANCH} to {DEV_BRANCH}:

abc1234 2.77.0
def5678 Merge pull request #679 from org/release/2.77.0
ghi9012 [Fix] Hotfix 

*[truncated — see source for full prompt]*