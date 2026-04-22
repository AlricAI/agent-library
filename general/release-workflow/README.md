# Release Workflow

> This repo owns the release workflow for `com.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ECS2D Renderer Release Workflow

This repo owns the release workflow for `com.ecs2d.renderer`.

## Goal

Create a new package release without manual file editing, manual version bumping, or manual tag handling.

## Agent workflow

From the repo root, run:

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\release-package.ps1 -Version 1.0.6 -Push -CreateGithubRelease
```

If the agent should also push the commit and tag to GitHub, keep `-Push`.
If it should prepare the release locally first, omit `-Push`.
If it should also create a GitHub release with auto-generated package-scoped changelog notes, add `-CreateGithubRelease` (requires `-Push`).

## What the script does

1. Validates that the version looks like `x.y.z`
2. Validates that the git tag `v<version>` does not already exist
3. Updates `Packages/com.ecs2d.renderer/package.json`
4. Stages the package directory and the repo-level README.md for the release commit
5. Creates a release commit
6. Creates an annotated tag `v<version>`
7. Optionally pushes `HEAD` and the tag together
8. Optionally creates a GitHub release with package-scoped changelog notes (generated from commits under `Packages/com.ecs2d.renderer/`)

## Preconditions

- Run from the `ECS2DTest` repo root
- Close Unity before running the script
- The package changes that belong in the release must already be present under `Packages/com.ecs2d.renderer`
- Do not rely on untracked files outside the package folder; they are intentionally ignored by the script
- The staged index must not contain unrelated files; the script fails if it finds them
- Releases are only allowed from `main` or `master`

## Safety behavior

- The script fails if the target tag already exists locally or on `origin`
- The script only stages the package folder and `README.md`, so scene/layout/test noise outside those paths is not pulled into the release commit
- The script fails if the package folder has no staged diff after the version update, to avoid empty release

*[truncated — see source for full prompt]*