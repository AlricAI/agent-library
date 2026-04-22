# PR Creation and Management Guidelines

> description: Pull request creation guidelines and workflow globs: [] scopes:

## System Prompt
---
description: Pull request creation guidelines and workflow
globs: []
scopes:
  - git
  - workflow
  - documentation
alwaysApply: false
---

# PR Creation and Management Guidelines

## Overview
This document outlines the standardized process for creating and managing pull requests, including hotfix workflows, PR description formatting, and cleanup procedures.

## 🔄 Workflow Steps

### 1. Branch Creation
```bash
# For hotfixes
git checkout qa
git pull origin qa
git checkout -b hotfix/descriptive-name

# For features
git checkout main
git pull origin main
git checkout -b feature/descriptive-name
```

### 2. PR Description Creation
```bash
# Create temporary description file
printf '# 🚑 [PR Type]: Brief Title\n\n## 🔍 Issue\n[Issue description]\n\n## 🛠 Fix\n[Fix description]\n\n## 📋 Changes\n- [Change 1]\n- [Change 2]\n\n## 🧪 Testing\n- [ ] [Test item 1]\n- [ ] [Test item 2]\n\n## ⏰ Created\n%s\n\n#Tags #MoreTags' "$(date +'%A, %B %d, %Y at %I:%M:%S %p')" > /tmp/pr_description.md
```

### 3. PR Creation Using GitHub CLI
```bash
# Create new PR
gh pr create --base [target_branch] --head [source_branch] --title "[PR Title]" --body-file /tmp/pr_description.md

# Update existing PR
gh pr edit [PR_NUMBER] --body-file /tmp/pr_description.md
```

### 4. Cleanup
```bash
# Remove temporary files
rm /tmp/pr_description.md
```

## 📝 PR Description Templates

<!-- markdownlint-disable MD025 -->
<!-- Note: H1 headings in templates below are intentional examples for PR descriptions -->

### Hotfix Template
\`\`\`markdown
# 🚑 Hotfix: [Brief Description]

## 🔍 Issue
[Describe the issue being fixed]

## 🛠 Fix
[Describe the fix implemented]

## 📋 Changes
- [Change 1]
- [Change 2]

## 🧪 Testing
- [ ] [Test step 1]
- [ ] [Test step 2]

## ⏰ Created
[DATE]

#Hotfix #[AdditionalTags]
\`\`\`

### Feature Template
\`\`\`markdown
# ✨ Feature: [Brief Description]

## 🎯 Purpose
[Describe the feature's purpose]

## 📋 Changes
- [Change 1]
- [Change 2]

## 🧪 Testing
- [ ] [Test ste

*[truncated — see source for full prompt]*