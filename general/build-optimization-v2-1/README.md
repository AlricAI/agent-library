# Build Optimization V2

> ## Context

After the V1 optimizations (PR #5719), which improved build times from ~18m to ~12m with OG image caching and parallel generation, CI buil

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Build Optimization V2 — CI Performance Analysis & Fixes

## Context

After the V1 optimizations (PR #5719), which improved build times from ~18m to ~12m with OG image caching and parallel generation, CI builds were still taking ~11 minutes. Local builds were much faster (~40s warm cache), indicating the CI slowdown was environment-specific.

## CI Log Analysis

From the CI run logs (main branch, after V1 optimizations):

| Phase | CI Time | Local Time | Ratio |
|-------|---------|------------|-------|
| Clean | 9ms | 6ms | ~1.5x |
| Glob | 47ms | 32ms | ~1.5x |
| **Parse (4 threads)** | **11 min** | **30s** | **~22x** |
| Filter | 2ms | 2ms | 1x |
| Emit (warm cache) | 11s | 11s | ~1x |
| OG Images (cached) | 6.2s | 5.5s | ~1.1x |
| **Total** | **~11 min** | **~40s** | **~16x** |

The **parse step** was the sole remaining bottleneck — 11 minutes in CI vs 30 seconds locally, a 22x slowdown.

## Root Cause: Per-File Git Date Lookups

### The Problem

The `CreatedModifiedDate` transformer plugin (`quartz/plugins/transformers/lastmod.ts`) uses `@napi-rs/simple-git` to get the last modification date for each file:

```typescript
// Called once PER FILE (2,348 times) inside worker threads
modified ||= await repo.getFileLatestModifiedDateAsync(relativePath)
```

**Why this is slow in CI:**
1. Each call traverses git history to find the file's last commit
2. With `fetch-depth: 0` (full history), each lookup scans potentially thousands of commits
3. `@napi-rs/simple-git` uses native bindings (libgit2) that have overhead in Docker containers
4. Running 2,348 individual git operations in parallel worker threads creates I/O contention
5. The Docker container (`node:20-bullseye-slim`) has limited I/O performance

### Locally vs CI

Locally, git operations are fast because:
- The `.git` directory is on a fast local filesystem (often SSD with hot page cache)
- No Docker filesystem layer overhead
- OS-level caching of git pack files is warm

In CI (Docker on GitHub Actions):
- Co

*[truncated — see source for full prompt]*