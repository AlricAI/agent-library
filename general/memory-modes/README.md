# Memory Modes

> Set `MEMORY_MODE` in `.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory System Modes

Set `MEMORY_MODE` in `.env`:

```bash
export MEMORY_MODE=solo   # or team, or pro
```

## Why Three Modes?

Different teams have different needs. A solo developer prototyping on a laptop shouldn't need Docker containers for authentication. A team of 10 agents across 3 machines needs shared context and identity. An enterprise deployment needs signed writes and access control. The three modes let you start simple and add capability as needed — no data migration, no breaking changes.

## Feature Comparison

| Feature | Solo | Team | Pro |
|---|:---:|:---:|:---:|
| **Infrastructure** | Ollama + Qdrant | Same | + Aries Docker |
| **Optional Add-ons** | — | Pulsar (events) | Pulsar (events) |
| Vector + hybrid search | ✅ | ✅ | ✅ |
| Semantic cache | ✅ | ✅ | ✅ |
| BM25 keyword search | ✅ | ✅ | ✅ |
| Developer identity tagging | — | ✅ | ✅ |
| Agent identity tagging | — | ✅ | ✅ |
| Shared team memory (`--shared`) | — | ✅ | ✅ |
| Developer isolation (private by default) | — | ✅ | ✅ |
| Real-time events (Pulsar) | — | ✅ | ✅ |
| W3C DID identity (Aries) | — | — | ✅ |
| Signed writes (HMAC-SHA256) | — | — | ✅ |
| Hash anchoring (tamper detection) | — | — | ✅ |
| Project access control | — | — | ✅ |
| Audit trail | — | — | ✅ |

> **Tested:** All features in this table have passing tests. Solo/Team: 15/15 multi-tenancy tests. Pro: 36/36 blockchain auth tests. Events: 19/19 agent events tests.

## When to Use Each Mode

### 🟢 Solo — Single Developer, One Machine

**Choose this when:** You're the only user, there's one agent, and you don't need access control.

**What you get:** Full vector + hybrid search, semantic caching, BM25 keyword matching. No identity overhead — every memory is yours.

**What you skip:** No developer/agent tagging, no shared memory, no signing, no events.

```bash
MEMORY_MODE=solo
python3 execution/session_boot.py --auto-fix
# Output: ✅ Memory system ready — N memories, N cached responses
#         Mode: Solo (single user)
```

### 🔵

*[truncated — see source for full prompt]*