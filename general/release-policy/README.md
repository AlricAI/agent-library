# Release Policy

> ## Purpose

This document defines when and how Olivia releases happen. It provides concrete criteria so the VP of Product can assess release readiness

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Release Policy

## Purpose

This document defines when and how Olivia releases happen. It provides concrete criteria so the VP of Product can assess release readiness and the Founding Engineer knows when to prepare an upstream PR.

## Git Workflow Context

- `origin/main` (`loveandrobots/olivia`) is the development trunk. All agent branches merge here.
- `upstream/main` (`LoveAndCoding/olivia`) is the canonical repo. PRs from `origin/main` to `upstream/main` are releases.
- CI on `upstream` handles TestFlight upload after merge.
- The board merges upstream PRs.

## Versioning

Olivia follows [Semantic Versioning](https://semver.org/):

| Bump | When | Examples |
|------|------|----------|
| **PATCH** (0.x.**Y**) | Bug fixes, copy corrections, non-functional changes that don't add features | Fix crash on empty inbox, correct reminder timezone display |
| **MINOR** (0.**Y**.0) | New user-facing features or meaningful enhancements to existing features | Add landscape orientation, add shared lists workflow |
| **MAJOR** (**Y**.0.0) | Reserved for App Store public launch (1.0.0). Not used during TestFlight pre-release. | 1.0.0 = first public App Store release |

Rules:
- During the 0.x.y pre-release phase, MINOR bumps are the normal cadence for feature work.
- PATCH bumps are appropriate for fixes that ship between feature releases.
- The Founding Engineer bumps the version in `package.json` and adds the changelog entry in the same PR as the release.
- Tags (e.g., `v0.2.0`) are applied by the board after merge. Agents do not tag.

## Release Criteria

A release is warranted when **any** of the following are true:

### 1. Feature completion
One or more user-facing features have been merged to `origin/main` and are ready for household use. This is the most common trigger.

**Checklist:**
- [ ] All acceptance criteria from the feature spec pass
- [ ] Tests pass (no regressions in existing test suite)
- [ ] No known critical or high-severity bugs in the new feature
- [ ] U

*[truncated — see source for full prompt]*