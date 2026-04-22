# Agent Sandboxing

> Coding agents execute real commands.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Sandboxing

Coding agents execute real commands. Production coding agents will, at some point, try to do something destructive — intentional prompt injection, hallucinated `rm`, overly aggressive refactor, data-exfil via curl. Sandbox the blast radius before it matters, not after.

> _Pattern informed by Fabio Akita's ai-jail work ([akitaonrails.com](https://akitaonrails.com)), which evolved from a 170-line bubblewrap shell script into a Rust binary with per-project config and cross-platform sandbox primitives._

## When to sandbox

Not every agent run needs a sandbox. Use this heuristic:

- **Sandbox required**: the agent can execute shell, write files outside the repo, open network connections, or touch any path shared with other projects.
- **Sandbox nice-to-have**: the agent only reads the repo and emits text (review comments, summaries).
- **Skip**: pure Q&A with no tool access.

The cost of sandboxing is startup latency + configuration. The cost of not sandboxing is one bad prompt away from production impact. Default to "on" for any autonomy-enabled session.

## What a sandbox must enforce

1. **Filesystem scoping** — explicit allow-list of paths the agent can read/write. Everything outside is either invisible (no bind mount) or read-only. No `$HOME` by default.
2. **Network egress control** — deny all outbound by default, allow-list the registries + APIs the agent actually needs.
3. **Process isolation** — no access to host `/proc`, `/dev` beyond necessary devices, no host PID namespace.
4. **Ephemeral working state** — tmpfs for `/tmp` so crashes/escapes don't leave traces.
5. **Credential firewall** — `.env`, SSH keys, cloud credential files **never** mounted. If the agent needs a secret, pass it explicitly via env var after a human decision.

## Primitives to build on

- **Linux**: `bubblewrap` (unprivileged user namespaces; what Docker, Flatpak, and Akita's ai-jail all use under the hood). Faster than Docker for per-invocation sandboxes; no daemon

*[truncated — see source for full prompt]*