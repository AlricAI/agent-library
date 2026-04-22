# Phase C Analysis

> **Date:** 2025-12-15  
**Status:** 📋 ANALYSIS - Understanding what's needed

## Phase C Goal

Add extension-specific FILE filtering to complete the t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase C Implementation Plan: Extension-Specific File Filtering

**Date:** 2025-12-15  
**Status:** 📋 ANALYSIS - Understanding what's needed

## Phase C Goal

Add extension-specific FILE filtering to complete the three-level hierarchy:
1. **Repo level:** `--repo-csproj-file-contains` ✅ (Phase B)
2. **File level:** `--cs-file-contains` ⏳ (Phase C - THIS)
3. **Line level:** `--line-contains` ✅ (Already exists)

## Expected Features

From the plan document:
```bash
--cs-file-contains "text"   # C# files only
--js-file-contains "text"   # JavaScript files only
--py-file-contains "text"   # Python files only
# ... all extension variants
```

## Current Code Analysis

### ✅ ALREADY EXISTS: Extension-specific file-contains parsing

**Location:** `src/cycodgr/CommandLine/CycoGrCommandLineOptions.cs` (lines 70-81)

```csharp
else if (arg.StartsWith("--") && arg.EndsWith("-file-contains"))
{
    // Extract extension: --cs-file-contains → cs
    var ext = arg.Substring(2, arg.Length - 2 - "-file-contains".Length);
    var terms = i + 1 < args.Count() ? args.ElementAt(++i) : null;
    if (string.IsNullOrWhiteSpace(terms))
    {
        throw new CommandLineException($"Missing search terms for {arg}");
    }
    command.FileContains = terms!;
    command.Language = MapExtensionToLanguage(ext);
}
```

**What this does:**
- Matches pattern: `--EXTENSION-file-contains`
- Sets `FileContains` to the search text
- Sets `Language` to the mapped extension (e.g., "cs" → "csharp")

### ✅ Language filtering in GitHub search

**Location:** `src/cycodgr/Helpers/GitHubSearchHelpers.cs` (lines 412-415)

```csharp
if (!string.IsNullOrEmpty(language))
{
    args.Add("--language");
    args.Add(language);
}
```

**What this does:**
- Passes `--language LANG` flag to `gh search code`
- GitHub API filters results to only that language/file type

### ✅ Language passed from command

**Location:** `src/cycodgr/Program.cs` (line 343 in HandleCodeSearchAsync)

```csharp
var codeMatches = await CycoGr.

*[truncated — see source for full prompt]*