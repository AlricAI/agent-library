# LORE

> ## The Itch

January 2026. I'd been spending a lot of time with AI coding agents — Claude Code, mostly — and the thing that kept bugging me was that t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# The floop Origin Story

## The Itch

January 2026. I'd been spending a lot of time with AI coding agents — Claude Code, mostly — and the thing that kept bugging me was that they didn't remember. You'd correct an agent, it'd get it right for the rest of the session, and then next session it's back to square one. Same mistake, same correction, over and over.

There are ways to deal with this. You can put rules in an `AGENTS.md` file, or split them across multiple markdown files, but it's manual — you have to remember to add things, keep them up to date, and they just grow into these unwieldy walls of text. Memory tools exist for storing facts and preferences, which is great, but facts aren't really behaviors. Knowing "the user prefers tabs" is different from knowing "when writing Go tests, use table-driven tests with `t.Run()`." At least that's how I felt, whether that's true or not is a philosphical discussion.

I hadn't tried many of these tools if I'm being honest. They intruiged me, but something felt missing. This wasn't a gap analysis — it was more of a feeling. There was a disconnect between the corrections I was giving and the agent's ability to internalize them. It just had me thinking: what if corrections could become durable, context-aware behaviors that the agent actually carries forward?

That idea excited me enough to start building.

## The Graph

The thinking started taking shape around [Steve Yegge's Beads](https://github.com/steveyegge/beads) — a graph-structured issue tracking system. Seeing behaviors and corrections as nodes in a graph, connected by typed relationships (similar-to, learned-from, requires, conflicts) — that felt right. Not a flat list of rules, but a network where the connections carry meaning.

The first commit landed on January 25, 2026. Core models, a graph store, a CLI skeleton, and a learning pipeline came together within the first week. I started dogfooding immediately — floop was being built with floop, and every correction

*[truncated — see source for full prompt]*