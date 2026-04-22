# Landing Page Brief

> This document is the input brief for an agent (or designer) building the Livewire landing page.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Landing Page Brief — Livewire

This document is the input brief for an agent (or designer) building the Livewire landing page.
It covers positioning, messaging, features, tone, structure, and visual assets.

---

## What is Livewire?

Livewire embeds a Clojure nREPL server inside a running Spring Boot application.
It gives an AI coding agent (or a curious developer) a **live, stateful, introspectable
probe into the running JVM** — beans, queries, transactions, security context, and all.

The primary consumer is an **agentic coding assistant** (e.g. Claude Code via `clojure-mcp`).
Livewire is the bridge between static code reasoning and real runtime behaviour.

**One-liner:**
> *Stop guessing. Ask the running app.*

**Tagline (already in use):**
> *Live nREPL wire into your Spring Boot app. Dev only. You've been warned.*

---

## The Problem Being Solved

Modern Java/Kotlin Spring Boot development has a slow inner loop:

> **edit → restart → observe** — restarts cost 30 seconds to 2 minutes and destroy all
> in-memory state accumulated during a debugging session.

AI coding agents make this worse: they reason *statically* about Spring apps and guess at
runtime behaviour. They can read the code but cannot ask the running app what it's actually
doing.

Livewire closes this gap. With a live REPL wired into the JVM:
- The agent can probe beans, query the DB, trace SQL, and inspect entity mappings in real time.
- Hypotheses are tested immediately against the live system — not the static code.
- The feedback loop shrinks from minutes to seconds.

---

## Target Audience

**Primary:** Java/Kotlin Spring Boot developers who work alongside AI coding agents
(Claude Code, Cursor, Copilot, etc.) and want the agent to be able to actually *observe*
the running app rather than guess.

**Secondary:** Individual developers who want a Clojure-style REPL experience (live
introspection, safe mutation, SQL tracing) on top of their existing Spring Boot app —
without rewriting anything i

*[truncated — see source for full prompt]*