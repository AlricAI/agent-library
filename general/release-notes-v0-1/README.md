# RELEASE NOTES V0.1

> **Release Date:** January 2025

---

## What is Jambot?

Jambot is an **AI groovebox** — or at least, it's trying to be. It's a CLI tool where you tal

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Jambot v0.1 Release Notes

**Release Date:** January 2025

---

## What is Jambot?

Jambot is an **AI groovebox** — or at least, it's trying to be. It's a CLI tool where you talk to an agent that controls a modular synth rack — drum machines, bass synths, effects, a sequencer, the works. Think hardware groovebox meets Claude Code. (In theory.)

**The philosophy (aka dare to dream):**
- **Real tool, not just a toy.** Yes, you can say "make me a techno beat" and get something. But the *goal* is a production tool that grows with you — tweak parameters, build arrangements, develop your sound. Not just AI slop, but *your* music with AI assistance. We're not there yet. This is v0.1.
- **Agentic loop.** Like Claude Code, Jambot runs an agent loop. You talk, it thinks, it acts (programs patterns, tweaks synths, renders audio), you hear results, you refine. The agent has tools for everything — 65+ of them — and usually figures out what to call. Sometimes it gets confused. It's v0.1.
- **CLI-first (for now).** Terminal UI with real-time feedback. Web UIs exist for hands-on sound design, but the brain lives in your terminal.

This is our first public release. It's rough. Many things are broken. More things are untested. But the core mostly works and it makes real-ish music on good days.

**Projects save to:** `~/Documents/Jambot/projects/`
**Renders save to:** `~/Documents/Jambot/projects/{project}/renders/`

---

## The Loop

```
> make me a techno beat
[agent programs drums]
> add a bass line
[agent adds JB202]
> bounce
[renders WAV to ~/Documents/Jambot/project/renders/]
> analyze that
[agent runs spectral analysis, gives mixing feedback]
> the kick is muddy
[agent tweaks EQ or suggests fixes]
> bounce
```

That's the idea: talk, tweak, bounce, analyze, repeat. Whether it actually works smoothly... it's v0.1.

---

## Highlights

### Modular Architecture (v1) — The Idea, Anyway

The foundation of Jambot is *supposed to be* a **plugin-based instrument system**. Every synth

*[truncated — see source for full prompt]*