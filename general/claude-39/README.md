# CLAUDE

> **CS** = CTRL Shift — a private link-sharing feed for Kochi subscribers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CTRL Shift (CS) - Link Sharing System

**CS** = CTRL Shift — a private link-sharing feed for Kochi subscribers.

## What It Does

- Users share links via SMS → broadcasted to all CS subscribers
- Links are auto-fetched and summarized by AI
- Web UI at `ctrlshift.so/links` shows the feed with comments
- AI-powered search/chat to query the shared content

## Architecture

```
SMS Side (sms-bot/)
├── commands/cs.ts              # SMS command handlers
├── agents/cs-chat/index.ts     # AI chat agent (this folder)
└── lib/cs-content-fetcher.ts   # Async content fetch + summarization

Web Side (web/)
├── app/cs/page.tsx             # Web UI (React)
└── app/api/cs/
    ├── route.ts                # GET links
    ├── auth.ts                 # Session token utils
    ├── send-code/route.ts      # SMS verification
    ├── verify-code/route.ts    # Code verification
    ├── set-handle/route.ts     # Handle setup
    ├── chat/route.ts           # AI search endpoint
    ├── comment/route.ts        # Add comment
    ├── delete-comment/route.ts # Delete comment
    └── delete-post/route.ts    # Delete post
```

## SMS Commands

| Command | Description |
|---------|-------------|
| `CS <url>` | Share a link (broadcasts to subscribers) |
| `CS <url> your note` | Share with a comment |
| `CS <url> person: Name` | Tag a link as being "about" someone |
| `CS <text>` | Comment on recent link (30-min rolling window) |
| `CS KOCHI <question>` | AI-powered Q&A — broadcasts question + answer to all |
| `CS SUBSCRIBE` / `CS SUB` | Request invite (adds to waitlist) |
| `CS UNSUBSCRIBE` / `CS UNSUB` | Unsubscribe |
| `CS LIST` | See 5 most recent links |
| `CS HELP` | Show commands |
| `CS APPROVE <phone>` | **Admin only**: Approve waitlist request |
| `CS Y` / `CS OK` | **Admin only**: Approve most recent waitlist request |

**Invite-only system:**
- CS is invite-only. `CS SUBSCRIBE` adds user to waitlist
- Admin receives SMS notification for each invite request
- Admin approves via `CS APPR

*[truncated — see source for full prompt]*