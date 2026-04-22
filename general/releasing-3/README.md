# RELEASING

> Maintainer runbook for shipping Paperclip across npm, GitHub, and the website-facing changelog surface.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Releasing Paperclip

Maintainer runbook for shipping Paperclip across npm, GitHub, and the website-facing changelog surface.

The release model is now commit-driven:

1. Every push to `master` publishes a canary automatically.
2. Stable releases are manually promoted from a chosen tested commit or canary tag.
3. Stable release notes live in `releases/vYYYY.MDD.P.md`.
4. Only stable releases get GitHub Releases.

## Versioning Model

Paperclip uses calendar versions that still fit semver syntax:

- stable: `YYYY.MDD.P`
- canary: `YYYY.MDD.P-canary.N`

Examples:

- first stable on March 18, 2026: `2026.318.0`
- second stable on March 18, 2026: `2026.318.1`
- fourth canary for the `2026.318.1` line: `2026.318.1-canary.3`

Important constraints:

- the middle numeric slot is `MDD`, where `M` is the UTC month and `DD` is the zero-padded UTC day
- use `2026.303.0` for March 3, not `2026.33.0`
- do not use leading zeroes such as `2026.0318.0`
- do not use four numeric segments such as `2026.3.18.1`
- the semver-safe canary form is `2026.318.0-canary.1`

## Release Surfaces

Every stable release has four separate surfaces:

1. **Verification** — the exact git SHA passes typecheck, tests, and build
2. **npm** — `paperclipai` and public workspace packages are published
3. **GitHub** — the stable release gets a git tag and GitHub Release
4. **Website / announcements** — the stable changelog is published externally and announced

A stable release is done only when all four surfaces are handled.

Canaries only cover the first two surfaces plus an internal traceability tag.

## Core Invariants

- canaries publish from `master`
- stables publish from an explicitly chosen source ref
- tags point at the original source commit, not a generated release commit
- stable notes are always `releases/vYYYY.MDD.P.md`
- canaries never create GitHub Releases
- canaries never require changelog generation

## TL;DR

### Canary

Every push to `master` runs the canary path inside [`.github/workf

*[truncated — see source for full prompt]*