# Cycodgr Implementation Plan

> **Status**: Ready to implement  
**Created**: 2025-12-11  
**Goal**: Rename cycodgh → cycodgr and restructure with `repo` and `code` verbs

---

## Ov

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TODO: cycodgr Implementation Plan

**Status**: Ready to implement  
**Created**: 2025-12-11  
**Goal**: Rename cycodgh → cycodgr and restructure with `repo` and `code` verbs

---

## Overview

Rename `cycodgh` → `cycodgr` (cycod-github-repo / "dig for" repos) and restructure into two focused verbs with better defaults and output formats.

**Name significance**: 
- "cycod-github-repo" 
- "dig for" (digger) - wordplay on searching/digging through repos

---

## Phase 1: Restructure to `repo` and `code` Verbs

### 1.1: Rename Project
- [x] Rename folder: `src/cycodgh` → `src/cycodgr`
- [x] Rename csproj: `cycodgh.csproj` → `cycodgr.csproj`
- [x] Rename namespace: `CycoGh` → `CycoGr`
- [x] Rename all classes: `CycoGh*` → `CycoGr*`
- [x] Update branch name
- [x] Update README references
- [x] Update help files

### 1.2: Implement `cycodgr repo` Verb

**Purpose**: Search for repositories by name/description/topics

**Command**: `cycodgr repo <keywords> [options]`

**Default format**: `detailed` (not `url` - breaking change but more useful)

**Output example**:
```
https://github.com/dotnet/aspire | ⭐ 8.5k | C# | .NET Aspire for cloud-native apps
https://github.com/thangchung/practical-dotnet-aspire | ⭐ 412 | C# | Practical examples...
```

**Tasks**:
- [x] Create `RepoCommand.cs` (copy from SearchCommand, rename)
- [x] Remove old `SearchCommand.cs`
- [x] Update command line parser to recognize `repo` verb
- [x] Change default format from `url` to `detailed`
- [x] Keep existing formats: `url`, `table`, `json`, `csv`
- [x] Update help documentation

**Example usage**:
```bash
cycodgr repo "dotnet aspire" --max-results 10
cycodgr repo "ai agents" --format table
```

### 1.3: Implement `cycodgr code` Verb

**Purpose**: Search for code/files containing text

**Command**: `cycodgr code <keywords> [options]`

**Default format**: `detailed` - Match cycodmd/FindInFiles output style

**Output example**:
```markdown
# microsoft/vscode (⭐ 152k | TypeScript)

## src/vs/platform/agen

*[truncated — see source for full prompt]*