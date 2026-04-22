# Quick Start

> Get up and running with Docu in 5 minutes!

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Start Guide

Get up and running with Docu in 5 minutes! This guide covers the essentials to start creating AI-powered documentation.

## 🚀 5-Minute Setup

### Step 1: Prerequisites (2 minutes)

**Required:**
- ✅ VS Code 1.97.0+ installed
- ✅ GitHub Copilot subscription active
- ✅ GitHub Copilot extension installed

**Quick Check:**
1. Open VS Code
2. Press `Ctrl+Shift+I` (or `Cmd+Shift+I` on Mac)
3. GitHub Copilot Chat should open

### Step 2: Install Docu (1 minute)

**Option A: From Marketplace** (Coming Soon)
- Extensions → Search "Docu" → Install

**Option B: From VSIX**
- Download VSIX file
- `Ctrl+Shift+P` → "Extensions: Install from VSIX"
- Select the VSIX file

### Step 3: Verify Installation (1 minute)

1. Open Copilot Chat (`Ctrl+Shift+I`)
2. Type: `@docu`
3. You should see Docu respond!

### Step 4: Create Your First Document (1 minute)

```
@docu /new "My First Document"
```

**Success!** You should see:
- ✅ New document created
- ✅ File opened in VS Code
- ✅ Clickable link in chat

## 🎯 Essential Commands

### Document Creation
```bash
# Basic document
@docu /new "Document Title"

# With template
@docu /new "Product Requirements" --template prd

# In specific folder
@docu /new "User Guide" --path docs/
```

### Agent Management
```bash
# List agents
@docu /agent list

# Switch agent
@docu /agent set prd-creator

# Current agent
@docu /agent current
```

### Templates
```bash
# List templates
@docu /templates list

# Show template details
@docu /templates show prd

# Create custom template
@docu /templates create my-template --interactive
```

### Document Updates
```bash
# Update section
@docu /update --file README.md --section "Installation" "New content"

# Review document
@docu /review --file requirements.md --level normal
```

## 🤖 Meet the Agents

| Agent | Use When | Example |
|-------|----------|---------|
| **PRD Creator** 🎯 | Starting new products/features | `@docu /agent set prd-creator` |
| **Brainstormer** 💡 | Exploring ideas an

*[truncated — see source for full prompt]*