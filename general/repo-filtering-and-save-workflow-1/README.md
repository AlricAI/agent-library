# Repo Filtering And Save Workflow

> **Status**: 🚧 **IN PROGRESS** - Phase A & B Complete, Phase C Starting  
**Date**: 2025-12-15  
**Last Updated**: 2025-12-15

## Overview

This docum

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Repository Filtering and Save/Load Workflow

**Status**: 🚧 **IN PROGRESS** - Phase A & B Complete, Phase C Starting  
**Date**: 2025-12-15  
**Last Updated**: 2025-12-15

## Overview

This document defines the implementation plan for three-level filtering (repos → files → lines) and progressive refinement workflow in cycodgr. The feature enables surgical precision in GitHub searches by pre-filtering repositories before searching files, and supports saving/loading results for iterative refinement.

## Feature Phases

### Phase A: Core Repo Pre-Filtering (MVP)

**Status:** ✅ **IMPLEMENTED** (2025-12-15)

**Delivers:** Basic repository filtering and save/load workflow

**Features:**
1. `--repo-file-contains "text"` - Find repos containing files with specified text (any file type)
2. `--save-repos repos.txt` - Save found repositories to file (`owner/name` format, one per line)
3. `@repos.txt` syntax - Load repositories from file (verify/fix existing implementation)

**Success Criteria:**
- Can pre-filter GitHub search to specific repositories
- Can save repository list to flat text file
- Can reload saved repositories for subsequent searches
- Dramatically reduces noise and search time for focused queries

**Example Usage:**
```bash
# Find and save repos
cycodgr --repo-file-contains "Microsoft.Extensions.AI" --save-repos ai-repos.txt

# Reuse saved repos
cycodgr @ai-repos.txt --cs-file-contains "anthropic"
```

**Implementation Details:**
- Added `RepoFileContains` property to `SearchCommand`
- Added `--repo-file-contains` command-line parsing
- Implemented `SearchCodeForRepositoriesAsync` in `GitHubSearchHelpers` for two-stage GitHub search
- Integrated repo pre-filtering into `HandleSearchCommandAsync` 
- Added `SaveRepos` property to `CycoGrCommand` base class
- Added `--save-repos` command-line parsing
- Implemented `FormatAsRepoList` and `FormatCodeAsRepoList` formatters
- Verified `@repos.txt` loading (already existed in codebase)

**Files Modified:**
- `src/cy

*[truncated — see source for full prompt]*