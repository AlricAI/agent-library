# Browser Use Rollout Spec 2026 04 09

> Date: 2026-04-09

Status: Proposed

Owner: `blueprint-cto`

Execution owner: `webapp-codex`

## Goal

Define a concrete, low-risk rollout plan for usi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Browser Use Rollout Spec

Date: 2026-04-09

Status: Proposed

Owner: `blueprint-cto`

Execution owner: `webapp-codex`

## Goal

Define a concrete, low-risk rollout plan for using Browser Use with Hermes- and Blueprint-routed agents without turning Browser Use into a new default execution layer, a new source of truth, or an org-wide default capability.

## Decision

Blueprint may use Browser Use as an optional browser backend for a small number of low-risk, browser-dependent lanes.

Blueprint will not:

- make Browser Use a default capability for every Hermes agent
- introduce Browser Use as a new source of truth or control plane
- route financial, rights-sensitive, buyer-commitment, or workspace-mutation lanes through Browser Use by default
- allow Browser Use to silently replace API, MCP, Firestore, Notion, Paperclip, or repo-file authority

The default rule remains:

1. prefer direct API, MCP, repo, and system-evidence paths
2. use browser automation only when the needed evidence is behind a UI and no safer direct path exists
3. keep browser use isolated, approval-bounded, and lane-specific

## Why This Fits Repo Doctrine

This rollout follows existing repo rules:

- AI tooling is a support layer, not an architecture override
- no new primary services may be introduced implicitly
- Paperclip remains the execution and ownership record
- Hermes memory remains supportive, not authoritative
- browser/computer-use is for UI-dependent work only when no API or MCP path exists

This also fits the current narrow-automation strategy:

- `preview_diagnosis` is already one of the repo's initial low-risk optimization lanes
- the current task system already has explicit `tool_policy` controls, including `browser_fallback_allowed` and `isolated_runtime_required`
- the current runtime already supports screenshot/log artifact capture when a task is marked `browser` or `mixed`

## External Research Notes

Research checked on 2026-04-09:

- Hermes docs say Browser Use is a support

*[truncated — see source for full prompt]*