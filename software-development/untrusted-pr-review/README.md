# UNTRUSTED PR REVIEW

> Use this workflow when you want Codex or Claude to inspect a pull request that you do not want touching your host machine directly.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Untrusted PR Review In Docker

Use this workflow when you want Codex or Claude to inspect a pull request that you do not want touching your host machine directly.

This is intentionally separate from the normal Paperclip dev image.

## What this container isolates

- `codex` auth/session state in a Docker volume, not your host `~/.codex`
- `claude` auth/session state in a Docker volume, not your host `~/.claude`
- `gh` auth state in the same container-local home volume
- review clones, worktrees, dependency installs, and local databases in a writable scratch volume under `/work`

By default this workflow does **not** mount your host repo checkout, your host home directory, or your SSH agent.

## Files

- `docker/untrusted-review/Dockerfile`
- `docker/docker-compose.untrusted-review.yml`
- `review-checkout-pr` inside the container

## Build and start a shell

```sh
docker compose -f docker/docker-compose.untrusted-review.yml build
docker compose -f docker/docker-compose.untrusted-review.yml run --rm --service-ports review
```

That opens an interactive shell in the review container with:

- Node + Corepack/pnpm
- `codex`
- `claude`
- `gh`
- `git`, `rg`, `fd`, `jq`

## First-time login inside the container

Run these once. The resulting login state persists in the `review-home` Docker volume.

```sh
gh auth login
codex login
claude login
```

If you prefer API-key auth instead of CLI login, pass keys through Compose env:

```sh
OPENAI_API_KEY=... ANTHROPIC_API_KEY=... docker compose -f docker/docker-compose.untrusted-review.yml run --rm review
```

## Check out a PR safely

Inside the container:

```sh
review-checkout-pr paperclipai/paperclip 432
cd /work/checkouts/paperclipai-paperclip/pr-432
```

What this does:

1. Creates or reuses a repo clone under `/work/repos/...`
2. Fetches `pull/<pr>/head` from GitHub
3. Creates a detached git worktree under `/work/checkouts/...`

The checkout lives entirely inside the container volume.

## Ask Codex or Claude to review it

*[truncated — see source for full prompt]*