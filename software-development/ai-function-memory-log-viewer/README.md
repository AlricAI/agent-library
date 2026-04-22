# Ai Function Memory Log Viewer

> ## Overview

Add a new AI function tool that allows the AI to inspect its own in-memory logging during execution. This will help with debugging when t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Function: Memory Log Viewer

## Overview

Add a new AI function tool that allows the AI to inspect its own in-memory logging during execution. This will help with debugging when the AI is writing code or troubleshooting issues in this repository.

## Background

The codebase uses a `MemoryLogger` that stores logs in a circular buffer (max 10,000 lines) with thread-safe access. Currently there's no way for the AI to inspect these logs during execution, which would be valuable for debugging AI function calls and execution flow.

## Implementation Plan

### 1. Architecture Decision: Direct Processing Pattern

**Analysis**: After examining existing AI function implementations, there are two patterns:
- **Pattern 1 (Direct)**: ViewFile processes files inline with sophisticated filtering (range selection, removeAllLines, lineContains, context expansion)
- **Pattern 2 (External)**: SearchInFiles delegates to cycodmd external process via CycoDmdCliWrapper

**Decision**: Use **Pattern 1 (Direct Processing)** because:
- Memory logs are already in memory (no file I/O needed)
- Simple operations similar to ViewFile
- Avoid process spawning overhead
- Direct control over thread safety
- Can reuse ViewFile's proven filtering pipeline exactly

### 2. Create New AI Function Tool

**File**: `src/cycod/FunctionCallingTools/MemoryLogHelperFunctions.cs`

**Class Structure**:
```csharp
using System.ComponentModel;
using System.Text.RegularExpressions;
using System.Text;

public class MemoryLogHelperFunctions
{
    [ReadOnly(true)]
    [Description("Get current in-memory logs with filtering and range selection for debugging AI function calls")]
    public string GetMemoryLogs(
        [Description("Start log line number (1-indexed). Negative numbers count from end (-1 = last line). Default: 1")] int startLine = 1,
        [Description("End log line number. 0 or -1 = end of logs. Negative numbers count from end. Default: 0")] int endLine = 0,
        
        [Description("Only show 

*[truncated — see source for full prompt]*