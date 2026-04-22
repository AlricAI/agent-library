# Jira Agent Workflow

> description: Jira automation workflow and guardrails for the agent globs: alwaysApply: false

## System Prompt
---
description: Jira automation workflow and guardrails for the agent
globs:
alwaysApply: false
---
# Jira Agent Workflow

Use this rule whenever the user asks us to “work on X” or otherwise signals that Jira + GitHub automation is required. The goal is to keep Jira, branches, and PRs fully synced without duplicating work.

## Default Flow
1. **Search Jira first.** Look up existing issues by summary, custom tags, or fuzzy match. Only create a new ticket if nothing relevant exists.
2. **Populate every field** when creating issues: summary, description, acceptance criteria, component, estimate, labels, reporter.
3. **Create a branch** that matches team naming: `JIRA-KEY-short-desc` (e.g., `PROJ-123-add-sso`).
4. **Push the branch and open a PR** titled `JIRA-KEY — Short Summary`. Link the Jira issue in the PR body and state the semantic-release impact (`feat`, `fix`, etc.).
5. **Link both ways.** Ensure Jira shows the PR/branch (GitHub for Jira handles this when keys are present). If not, add a remote link via REST API.
6. **Transition workflow states.**
   - When the PR opens: move Jira to *In Progress* and optionally comment.
   - When the PR merges (CI green): move Jira to *Done* or *Ready for QA* and add a comment referencing commits/PR.

## Semantic Versioning Expectations
- The repo uses semantic-release with the Conventional Commits parser defined in `backend/.releaserc.js`, so every merge commit (usually via squash) must follow `JIRA-KEY type(scope): subject`.
- Valid `type` values include `feat`, `fix`, `docs`, `bugfix`, `chore`, etc. Pick the one that drives the correct version bump.
- PR descriptions must call out the intended `type` and `scope` so reviewers know what release section the change will land in.
- If a PR bundles multiple logical changes, split them so each PR has a single semantic-release type.
- When approving, confirm the squash-merge commit message keeps both the Jira key and the Conventional Commit header (e.g., `TT-22 feat(ci): enforce j

*[truncated — see source for full prompt]*