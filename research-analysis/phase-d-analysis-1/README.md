# Phase D Analysis

> **Date:** 2025-12-15  
**Status:** ✅ READY TO IMPLEMENT - Decisions made

## Final Decisions

### 1. Flag Names: Singular vs Plural Pattern

Following

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase D Implementation Plan - FINAL DECISIONS

**Date:** 2025-12-15  
**Status:** ✅ READY TO IMPLEMENT - Decisions made

## Final Decisions

### 1. Flag Names: Singular vs Plural Pattern

Following existing `--repo` / `--repos` pattern:

**Singular (one value):**
- `--file-path src/Program.cs` - Single file path

**Plural (multiple values or @file):**
- `--file-paths src/Program.cs src/Startup.cs` - Multiple paths
- `--file-paths @files-microsoft-semantic-kernel.txt` - Load from file

### 2. Save Flags with Template Support

**Pattern:** Like `--save-chat-history [template]` with defaults

**Flags:**
- `--save-file-paths [template]` 
  - Default: `files-{repo}.txt`
  - Creates one file per repo with relative paths
  - Example: `files-microsoft-semantic-kernel.txt`
  
- `--save-repo-urls [template]`
  - Default: `repo-urls.txt`
  - Clone URLs: `https://github.com/owner/repo.git`
  
- `--save-file-urls [template]`
  - Default: `file-urls-{repo}.txt`
  - Blob URLs: `https://github.com/owner/repo/blob/main/src/file.cs`

**Template variables:** `{repo}`, `{time}`, etc.

### 3. File Paths Format: Repo-Relative

**Saved format** (in `files-{repo}.txt`):
```
src/Kernel.cs
src/Extensions/KernelExtensions.cs
Models/User.cs
```

**NOT qualified** (no `owner/repo:` prefix)

**Why:** 
- One file per repo via template
- Cleaner, simpler paths
- Must be used with `--repo` to provide context

### 4. Usage Pattern

**Discovery phase:**
```bash
cycodgr --repo-csproj-file-contains "Microsoft.Extensions.AI" \
        --cs-file-contains "Anthropic" \
        --save-repos repos.txt \
        --save-file-paths
```

**Creates:**
- `repos.txt` - List of repo names
- `files-microsoft-semantic-kernel.txt` - Relative paths for that repo
- `files-dotnet-aspnetcore.txt` - Relative paths for that repo
- etc.

**Refinement phase:**
```bash
cycodgr --repo microsoft/semantic-kernel \
        --file-paths @files-microsoft-semantic-kernel.txt \
        --line-contains "Configure" \
        --lines 3

*[truncated — see source for full prompt]*