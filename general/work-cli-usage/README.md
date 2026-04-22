# work-cli-usage

> Guide for using the work CLI to manage work items across multiple backends (GitHub, Jira, Linear, Azure DevOps, local filesystem). Use when working with work item management, task tracking, project coordination, CLI automation, or any work CLI commands like create, list, edit, start, close, context, auth, notify, or schema operations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Work CLI Usage

## Overview

The work CLI is a unified, stateless command-line tool for managing work items across multiple project management backends. It enables seamless work item management whether you're working with GitHub Issues, local filesystem, or planning to integrate with Jira, Linear, or Azure DevOps.

## Quick Start

### Local Filesystem (No External Dependencies)

```bash
# Create and set context
work context add my-project --tool local-fs --path ./work-items
work context set my-project

# Start creating work items immediately
work create "Set up project structure" --kind task --priority medium
work list
```

### GitHub Integration

```bash
# Authenticate with GitHub CLI (recommended)
gh auth login

# Create GitHub context
work context add my-project --tool github --url https://github.com/owner/repo
work context set my-project
work auth login

# Create work items that appear as GitHub issues
work create "Fix login bug" --kind bug --priority high
```

## Core Operations

### 1. Lifecycle Management

Manage work item states through their lifecycle:

```bash
# Create work items
work create "Title" --kind task --priority medium --assignee username
work create "Bug description" --kind bug --priority critical

# Manage state transitions
work start ITEM-123        # new → active
work close ITEM-123        # active/new → closed
work reopen ITEM-123       # closed → active
```

### 2. Querying and Access

Find and retrieve work items with powerful filtering:

```bash
# Get specific item
work get ITEM-123

# List with filters
work list                                    # All items
work list where state=active                 # Active items only
work list where priority=high and state=new  # High priority new items
work list where assignee=me order by priority desc
work list where kind=bug limit 10
```

### 3. Attribute Management

Update work item properties:

```bash
# Set attributes
work set ITEM-123 priority=high assignee=alice
work set ITEM-123 title="Ne

*[truncated — see source for full prompt]*