# Multi Repo

> > Library changes before consumer changes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Repository AI Workflows

> Library changes before consumer changes. Release before import. Test cross-repo impact.

## The Problem

Modern development spans multiple repositories: shared libraries, microservices, frontend/backend splits. AI agents work well within a single repo but struggle with multi-repo coordination. They update a library but forget to update consumers. They release in the wrong order, breaking dependency chains. They miss cross-repo breaking changes.

The result: broken builds, version mismatches, deployment failures, and hours debugging why "it worked in isolation."

The insight: Multi-repo work requires explicit coordination, dependency ordering, and cross-repo context. AI agents can help, but you must orchestrate.

## The Pattern

### Dependency Ordering: Bottom-Up Releases

Changes flow from foundation to consumers, never the reverse.

**Dependency chain:**
```
forge-patterns (core library)
    ↓
generator (code generator, uses forge-patterns)
    ↓
app (web app, uses generator)
```

**Release order (bottom-up):**
```
1. forge-patterns: v1.5.0 (new feature)
2. generator: v0.8.0 (uses forge-patterns@^1.5.0)
3. app: v0.30.0 (uses generator@^0.8.0)
```

**Wrong order (breaks everything):**
```
1. app: import { newFeature } from 'generator'
   ERROR: newFeature doesn't exist in generator@0.7.0

2. generator: import { helper } from 'forge-patterns'
   ERROR: helper doesn't exist in forge-patterns@1.4.0

3. forge-patterns: export const helper = ...
   (Too late, consumers already broke)
```

**Automated dependency check:**
```bash
#!/bin/bash
# check-release-order.sh

# Get repos in dependency order (bottom to top)
repos=("forge-patterns" "generator" "app")

for repo in "${repos[@]}"; do
  cd ~/"$repo" || exit

  # Check for unreleased changes
  if ! git diff --quiet HEAD origin/main; then
    echo "ERROR: $repo has unreleased changes. Release before proceeding."
    exit 1
  fi

  # Check dependencies are released
  if [ -f package.json ]

*[truncated — see source for full prompt]*