# Todo File Search Replace Tool Improvements

> ## Summary
Improve the file discovery and replacement tools to reduce user confusion and add bulk replacement capabilities.

## Current Issues

### Qu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TODO: File Search and Replace Tool Improvements

## Summary
Improve the file discovery and replacement tools to reduce user confusion and add bulk replacement capabilities.

## Current Issues

### QueryFiles Confusion
- **Problem**: `QueryFiles` mixes file discovery with content display, causing confusion when users want file paths but get content output
- **Evidence**: User experience shows frequent confusion when looking for files vs searching within files
- **Parameter Analysis**: About half of QueryFiles parameters are irrelevant for file-discovery-only use cases

### ReplaceOneInFile Limitations  
- **Problem**: `ReplaceOneInFile` only works on single files with literal strings
- **Gap**: No bulk replacement capability across multiple files
- **Workaround**: Users fall back to shell commands for bulk operations

## Proposed Solution

### Split QueryFiles into Focused Tools

**FindFiles** (File Discovery)
```
FindFiles(filePatterns, excludePatterns, fileContains, fileNotContains, 
          modifiedAfter, modifiedBefore, maxFiles)
→ Output: File paths only
```

**SearchInFiles** (Content Search)  
```
SearchInFiles(filePatterns, excludePatterns, fileContains, fileNotContains,
            modifiedAfter, modifiedBefore, searchPattern, lineContains, 
            removeAllLines, linesBeforeAndAfter, lineNumbers,
            maxFiles, maxCharsPerLine, maxTotalChars)
→ Output: File content with highlighted matches
```

### Add Bulk Replacement Tool

**ReplaceAllInFiles** (Bulk Replacement)
```
ReplaceAllInFiles(filePatterns, excludePatterns, fileContains, fileNotContains,
                  modifiedAfter, modifiedBefore, maxFiles,
                  old, new, useRegex=false, preview=true)
→ Bulk replacement with safety features
```

## Design Decisions Made

### Display Format
- **Git diff style** with `-`/`+` prefixes for removed/added lines
- **Grouped format**: All removed lines together, then all added lines together
- **Context lines**: Show surrounding code for 

*[truncated — see source for full prompt]*