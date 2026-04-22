# Discovery Agents

> How to create AI agents that lead people through building, reviewing, and updating their Context Stack on any platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Discovery Agents

How to create AI agents that lead people through building, reviewing, and updating their Context Stack on any platform.

A discovery agent is not a prompt you paste and forget. It is a persistent, reusable system that interviews someone, drafts their context files, refines them through feedback, and can be returned to later for updates. This guide covers how to build that system on every major AI platform, with platform-specific optimizations that make the experience better than a raw prompt paste.


## The Discovery System

Every discovery agent, regardless of platform, needs to do five things:

1. **Orient.** Explain what the Context Stack is, what the session will produce, and how long it will take.
2. **Interview.** Ask questions one at a time, probe for specifics, and adapt based on answers.
3. **Draft.** Generate structured context files using the person's actual language.
4. **Refine.** Present drafts for correction, incorporate feedback, and check consistency across files.
5. **Hand off.** Explain what to do with the finished files: where to save them and how to load them.

The three discovery tiers handle this at different depths:

| Tier | Time | Components | Best For |
|:-----|:-----|:-----------|:---------|
| Quick Start | 5 minutes | 3 core files | First-time users, quick proof of concept |
| Guided Session | 30-45 minutes | All 12 files | Most professionals, recommended starting point |
| Deep Dive | 60-90 minutes | All 12 files + loading recommendations | Power users who want maximum precision |

The prompt for each tier is in the `discovery/` directory:
- `discovery/quick-start.md`
- `discovery/context-discovery-session.md`
- `discovery/deep-dive.md`

The update prompt for refreshing existing context is in:
- `discovery/context-update-session.md`


## Two Ways to Use the Discovery Prompts

### Option A: Paste Into a Conversation

Open any AI assistant. Paste the discovery prompt as your first message. The session starts immediatel

*[truncated — see source for full prompt]*