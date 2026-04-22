# Release Notes

> Enhance GitHub release with detailed notes after release PR is merged to main

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping enhance a GitHub release with comprehensive release notes. This command should be run AFTER the release PR has been merged to the production branch.

## Step 1: Load Configuration

Check for configuration:

```bash
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
workflow:
  productionBranch: main
versioning:
  file: auto
release:
  generateChangelog: true
  changelogCategories:
    - name: "Bug Fixes"
      prefixes: ["[Fix]", "[FIX]", "fix:"]
      emoji: "bug"
    - name: "Features"
      prefixes: ["[Feature]", "feat:"]
      emoji: "sparkles"
```

**Default Values:**

```yaml
workflow:
  productionBranch: main
versioning:
  file: auto
```

## Step 2: Verify Current State

Check that you're on the production branch and up-to-date:

```bash
PROD_BRANCH=$(config.workflow.productionBranch || "main")

# Get current branch
CURRENT=$(git branch --show-current)

# Pull latest
git pull origin ${PROD_BRANCH}
```

**Validation:**

- If not on production branch:
  ```
  You should be on {PROD_BRANCH} branch after the release PR is merged.
  Run: git checkout {PROD_BRANCH} && git pull
  ```

## Step 3: Get Current Version

Detect version file and read current version:

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
fi

TAG_NAME="v${VERSION}"
```

Display to user:

```
Current version: {VERSION}
Release tag: v{VERSION}
```

## Step 4: Check if Release Exists

```bash
gh release view v${VERSION} 2>&1
```

**Possible States:**

1. Release exists → Will update with enhanced notes
2. Release doesn't exist → Will create new release
3. Tag doesn't exist → Error, release 

*[truncated — see source for full prompt]*