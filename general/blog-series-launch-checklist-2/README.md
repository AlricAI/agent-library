# Blog Series Launch Checklist

> ## 🎯 Overview

📋 This checklist covers everything that must be included in a PR to launch a new auto blog series. 🔧 The auto-discovery architecture

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🚀 Blog Series Launch Checklist

## 🎯 Overview

📋 This checklist covers everything that must be included in a PR to launch a new auto blog series. 🔧 The auto-discovery architecture means zero Haskell code changes are needed, but several files must be created and several documentation files must be updated.

## ✅ PR Checklist

### 📦 Required New Files

- [ ] **`haskell/series/{series-id}.json`** — Series configuration with name, icon, priorityUser, scheduleHourPacific, and models
- [ ] **`{series-id}/AGENTS.md`** — System prompt defining the series identity, voice, editorial standards, post structure, topics, and recap guidelines. Must include YAML frontmatter with share, no_social, title, URL, Author, and tags fields
- [ ] **`{series-id}/YYYY-MM-DD-slug.md`** — Inaugural seed post written by the PR author (not auto-generated). This gives the series a first post so the automation has context for subsequent posts. Must follow the standard frontmatter format with title, URL, Author, aliases, and navigation breadcrumb
- [ ] **`specs/{series-id}.md`** — Product and engineering spec documenting the series overview, architecture, configuration, post structure, schedule, editorial standards, recaps, topics, testing, and files

### 📝 Required Documentation Updates

- [ ] **`README.md`** — Four updates needed:
  - Content Organization table: add row for `{series-id}/` directory
  - Scheduled Tasks table: add row with Pacific hour and description
  - Configuration Variables table: add `{SERIES_ID}_PRIORITY_USER` env var
  - Specs table: add row linking to `specs/{series-id}.md`
- [ ] **`specs/blog-generation.md`** — Two updates needed:
  - Overview paragraph: increment the series count (e.g., four to five)
  - Blog Series Configuration table: add row with series ID, icon, schedule hour, priority user, and base URL
- [ ] **`specs/scheduled-tasks.md`** — Three updates needed:
  - Data Flow diagram: add `blog-series:{series-id}` line in the task list
  - Blog Series schedu

*[truncated — see source for full prompt]*