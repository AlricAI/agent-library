# Lightweight Code Review Process

> This document outlines our lightweight code review process for systematic review of files against our coding standards.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Lightweight Code Review Process

This document outlines our lightweight code review process for systematic review of files against our coding standards. This process complements our [comprehensive code review process](Code-Review-Process.md) by providing a structured approach to reviewing files against established style guidelines.

## Purpose

The lightweight code review process serves several key purposes:

1. **Systematic Identification**: Efficiently identify specific code style violations across the codebase
2. **Style Conformance**: Verify that files adhere to our [C# Coding Style Essential Guide](C%23-Coding-Style-Essential.md) 
3. **Precise Documentation**: Create a clear record of violations with exact line references for future correction
4. **Actionable Feedback**: Provide specific, implementable solutions for each identified issue
5. **Localized Reviews**: Keep review documentation alongside the source code for better discoverability

## Process Overview

### 1. Create a Master Review Checklist

First, create a master checklist of files to review, called `Files-To-Review.md`, in the root of your project repository. This checklist should include all files you plan to review.

````markdown
# Files to Review

## C# Source Files
- [ ] src/path/to/File1.cs
- [ ] src/path/to/File2.cs

## Documentation Files
- [ ] docs/SomeDoc.md
- [ ] docs/AnotherDoc.md

````

### File Selection Strategy

When creating your master checklist, consider these approaches for selecting files to review:

- **Branch Changes**: Include files modified in your current branch since it branched from main
- **Recent Changes**: Include files changed in the last few days or 24 hours
- **Personal Changes**: Focus on files you've recently modified yourself
- **High-Impact Areas**: Focus on core or critical code that would benefit most from style compliance

### 2. Review Each File

For each file in your master checklist:

1. **Create a review file** in the same directory as the source file u

*[truncated — see source for full prompt]*