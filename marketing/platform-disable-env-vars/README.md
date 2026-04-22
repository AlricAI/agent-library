# Platform Disable Env Vars

> ## Overview

Each social media platform (Twitter, Bluesky, Mastodon) can be explicitly disabled
via environment variables, even when valid credentials

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Platform Disable Environment Variables

## Overview

Each social media platform (Twitter, Bluesky, Mastodon) can be explicitly disabled
via environment variables, even when valid credentials are present. This is useful
when a platform's API becomes unreliable, a free tier is discontinued, or you simply
want to pause posting to a specific platform without removing credentials.

## Environment Variables

| Variable | Effect | Accepted Values |
|---|---|---|
| `DISABLE_TWITTER` | Disable Twitter/X posting | `true`, `1`, `yes` (case-insensitive) |
| `DISABLE_BLUESKY` | Disable Bluesky posting | `true`, `1`, `yes` (case-insensitive) |
| `DISABLE_MASTODON` | Disable Mastodon posting | `true`, `1`, `yes` (case-insensitive) |

Any other value (including empty string, `false`, `0`, `no`) keeps the platform enabled.

## How It Works

The `isPlatformDisabled(envVar)` function checks the value of the given environment
variable. If it matches one of the truthy values (`true`, `1`, `yes` — case-insensitive,
whitespace-trimmed), the platform is disabled.

In `validateEnvironment()`, each platform is disabled if:
1. The `DISABLE_*` env var is set to a truthy value, **OR**
2. The platform's required credentials are not all present.

When a platform is disabled via env var, a log message is emitted:
```
🚫 Twitter disabled via DISABLE_TWITTER env var
```

The platform's credentials object is returned as `null`, which causes all downstream
code (in `main()` and `getConfiguredPlatforms()`) to skip that platform entirely.

## GitHub Actions Configuration

The workflow (`.github/workflows/scheduled.yml`) passes these env vars from
GitHub repository variables:

```yaml
env:
  DISABLE_TWITTER: ${{ vars.DISABLE_TWITTER || '' }}
  DISABLE_BLUESKY: ${{ vars.DISABLE_BLUESKY || '' }}
  DISABLE_MASTODON: ${{ vars.DISABLE_MASTODON || '' }}
```

### Setting a Repository Variable

1. Navigate to your repository → **Settings** → **Secrets and variables** → **Actions**
2. Click the **Variables** ta

*[truncated — see source for full prompt]*