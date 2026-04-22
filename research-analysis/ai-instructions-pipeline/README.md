# Ai Instructions Pipeline

> **Status**: Not Started  
**Priority**: Medium  
**Reference**: cycodmd instructions feature

---

## Overview

Add AI-powered analysis to cycodgr sea

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TODO: AI Instructions Pipeline for cycodgr

**Status**: Not Started  
**Priority**: Medium  
**Reference**: cycodmd instructions feature

---

## Overview

Add AI-powered analysis to cycodgr search results, following cycodmd's instructions pattern.

**Goal**: Process search results through cycod for AI analysis at different levels:
1. Per-repository analysis (--repo-instructions)
2. Per-file analysis (--file-instructions, --EXT-file-instructions)
3. Aggregated output analysis (--instructions)

---

## Reference Implementation

**Study these files from cycodmd**:
- `cycodmd help instructions` - Main instructions help
- `cycodmd help file instructions` - File-level instructions
- `src/cycodmd/CommandLine/CycoDmdCommand.cs` - How instructions are stored (Tuple pattern!)
- `src/cycodmd/CommandLine/CycoDmdCommandLineOptions.cs` - How flags are parsed
- `src/cycodmd/Program.cs` - How instructions are executed with cycod

---

## Key Implementation Pattern (from cycodmd)

### Data Structure - The Tuple Pattern

```csharp
// In CycoDmdCommand.cs (lines 12-13):
public List<Tuple<string, string>> FileInstructionsList { get; set; } = new();
public List<string> InstructionsList { get; set; } = new();
```

**Why Tuple<string, string>?**
- First string: The instruction/prompt
- Second string: The file criteria (extension or pattern)
- Allows --cs-file-instructions to store `("review code", "cs")`
- Allows --file-instructions to store `("explain", "*")` for all files

**For cycodgr, we'll need**:
```csharp
// In SearchCommand.cs
public List<Tuple<string, string>> RepoInstructionsList { get; set; } = new();
    // Tuple: (instruction, repoCriteria)
    // Currently only "*" for all repos, but extensible for future filters

public List<Tuple<string, string>> FileInstructionsList { get; set; } = new();
    // Tuple: (instruction, fileExtension)
    // Example: ("analyze", "cs"), ("review", "rs"), ("explain", "*")

public List<string> InstructionsList { get; set; } = new();
    // S

*[truncated — see source for full prompt]*