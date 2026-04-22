# Manual Cleanup Refactor Guide

> ## Background

GitHub issue: `alibaba/OpenSandbox#442`

Issue summary:

- Support non-expiring sandboxes
- Let callers manage cleanup explicitly
- Kee

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Manual Cleanup Refactor Guide

## Background

GitHub issue: `alibaba/OpenSandbox#442`

Issue summary:

- Support non-expiring sandboxes
- Let callers manage cleanup explicitly
- Keep existing TTL-based behavior for current users
- Work across Docker and Kubernetes runtimes where supported

Current implementation does not support this. TTL is a hard requirement in:

- API request/response models
- Docker runtime scheduling and restore logic
- Kubernetes workload creation and renew flows

This document captures the recommended refactor direction before implementation starts.

## Refactor Goal

Introduce a manual cleanup mode without adding a new top-level mode field for now.

Chosen semantic:

- `timeout` present: sandbox uses TTL behavior
- `timeout` omitted or `null`: sandbox uses manual cleanup behavior

Non-goals for this refactor:

- Do not support magic values like `timeout=0` or `timeout=-1`
- Do not redesign the lifecycle API beyond what is required for manual cleanup
- Do not overload `renew_expiration` to switch a sandbox from manual mode back to TTL mode

## Compatibility and Rollout

This refactor is compatible through a controlled upgrade path, not through strict protocol backward compatibility.

Important compatibility fact:

- Once manual cleanup is enabled in an environment, lifecycle responses may contain `expiresAt=null`
- Lifecycle responses may also serialize other nullable fields explicitly as `null` instead of omitting them
- Older SDKs that assume `expiresAt` is always a timestamp may fail when they call `create`, `get`, or `list`
- Older schema-generated clients may also fail if they assume fields such as `metadata`, `status.reason`,
  `status.message`, or `status.lastTransitionAt` are always omitted or always non-null
- Existing TTL-based callers are unaffected as long as they do not encounter manual-cleanup sandboxes

Recommended rollout order:

1. Upgrade all SDKs/clients that read lifecycle API responses
2. Upgrade the server
3. Only then

*[truncated — see source for full prompt]*