# Code Review Example Simple Tools And Agents

> This document shows how to build up a complete code review system using the simple tools specification and markdown-based agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Review Example: Simple Tools and Agents

This document shows how to build up a complete code review system using the simple tools specification and markdown-based agents.

## Building Blocks: Basic Git Tools

### changed-files.yaml
```yaml
name: changed-files
description: Get list of files changed since master

bash: git diff --name-only {BASE_BRANCH}..HEAD

parameters:
  BASE_BRANCH:
    type: string
    description: Branch to compare against
    default: "master"

tags: [git, read]
platforms: [windows, linux, macos]
```

### file-diff.yaml
```yaml
name: file-diff  
description: Show diff for a specific file since master

bash: git diff {BASE_BRANCH}..HEAD -- "{FILE}"

parameters:
  FILE:
    type: string
    description: Path to the file to show diff for
    required: true
  BASE_BRANCH:
    type: string
    description: Branch to compare against  
    default: "master"

tags: [git, read]
platforms: [windows, linux, macos]
```

### all-diffs.yaml
```yaml
name: all-diffs
description: Show all diffs since master

bash: git diff {BASE_BRANCH}..HEAD

parameters:
  BASE_BRANCH:
    type: string
    description: Branch to compare against
    default: "master"

tags: [git, read]  
platforms: [windows, linux, macos]
```

## Analysis Tools

### analyze-file.yaml
```yaml
name: analyze-file
description: Analyze a single file for code quality issues

bash: |
  echo "=== File Analysis: {FILE} ==="
  echo "Lines of code:"
  wc -l "{FILE}"
  echo ""
  echo "File type:"
  file "{FILE}"
  echo ""
  echo "Recent changes:"
  git log --oneline -5 -- "{FILE}" || echo "No git history"

parameters:
  FILE:
    type: string
    description: Path to file to analyze
    required: true

tags: [analysis, read]
platforms: [windows, linux, macos]
```

### analyze-diff.yaml
```yaml
name: analyze-diff
description: Analyze diff content for patterns and complexity

python: |
  import sys
  diff_content = """{DIFF_CONTENT}"""
  
  lines = diff_content.split('\n')
  added_lines = [l for l in 

*[truncated — see source for full prompt]*