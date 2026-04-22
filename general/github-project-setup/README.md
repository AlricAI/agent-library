# GITHUB PROJECT SETUP

> This guide explains how to set up a GitHub Project (v2) board for ModPorter-AI with proper columns, labels, and automation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GitHub Project Board Setup Guide

This guide explains how to set up a GitHub Project (v2) board for ModPorter-AI with proper columns, labels, and automation.

## Overview

GitHub Projects (v2) is a flexible project management tool that integrates with issues and pull requests. This setup provides a Kanban-style workflow for tracking work on the ModPorter-AI project.

## Step 1: Create a New GitHub Project

1. Navigate to the [GitHub Projects page](https://github.com/orgs/anchapin/projects) or go to the repository's Projects tab
2. Click "New Project"
3. Select "New project" (not "New project (classic)")
4. Name the project: **ModPorter-AI Development**
5. Choose "Board" as the template (this gives us a Kanban-style layout)
6. Click "Create"

## Step 2: Set Up Kanban Columns

The default board comes with three columns. Modify them to match this workflow:

| Column | Description |
|--------|-------------|
| **Backlog** | Issues that need to be triaged or are not yet ready for work |
| **Ready** | Issues that are well-defined and ready to be picked up |
| **In Progress** | Issues currently being worked on |
| **Review** | Issues with open PRs or needing review |
| **Done** | Completed issues (closed) |

### How to Add/Edit Columns:

1. Click the "+" button next to the last column to add a new column
2. Click the "..." menu on a column to rename or delete it
3. Drag columns to reorder them

## Step 3: Configure Status Field

The Status field is the main field for tracking issue progress. Configure it with these options:

1. Click on the "..." menu in the project header
2. Select "Settings"
3. Under "Fields", find the "Status" field
4. Ensure the options match your column names:
   - Backlog
   - Ready
   - In Progress
   - Review
   - Done

## Step 4: Add Custom Fields

Add these custom fields to enhance project tracking:

### Priority Field
- Type: Single select
- Options:
  - `priority-1` (Critical)
  - `priority-2` (High)
  - `priority-3` (Medium)
  - `priority-4` 

*[truncated — see source for full prompt]*