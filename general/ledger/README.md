# Ledger

> The TraceCore Ledger is the trust-facing index for certified agents, signed evidence bundles, and registry-level provenance.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TraceCore Ledger

The TraceCore Ledger is the trust-facing index for certified agents, signed evidence bundles, and registry-level provenance.

This page is the operator entry point for the Ledger workflow. It explains how ledger snapshots relate to run artifacts and bundles, and which CLI verbs to use when you want to inspect, seal, verify, or audit evidence.

For the full registry schema, provenance field reference, and governance details, see:

- `docs/governance/ledger.md`
- `docs/governance/ledger_governance.md`

## What the Ledger is

The Ledger is a static registry stored at:

`agent_bench/ledger/registry.json`

It is not the same thing as a live run log.

- **Run artifacts** live in `.agent_bench/runs/`
- **Baseline bundles** live in `.agent_bench/baselines/`
- **Ledger entries** summarize trusted/certified evidence for known agents
- **Registry signatures** prove the top-level ledger snapshot has not been tampered with

In practice, the Ledger is the human-readable and machine-verifiable index that points at the evidence you produced with the run / verify / bundle workflow.

## Core workflow

A typical evidence flow looks like this:

```bash
tracecore run --agent agents/my_agent.py --task filesystem_hidden_config@1 --seed 0
tracecore verify --latest
tracecore bundle seal --latest
tracecore bundle status
tracecore ledger
tracecore ledger verify --registry
```

That flow gives you:

- a run artifact
- replay / strict verification surfaces
- a sealed bundle directory
- visibility into the current ledger registry and signed evidence state

## CLI verbs

### Inspect ledger entries

```bash
tracecore ledger
tracecore ledger --show toy_agent
tracecore ledger --show agents/toy_agent.py
```

Use this when you want to:

- list known ledger entries
- inspect the recorded tasks for an agent
- confirm which agent path or suite a certified entry belongs to

### Seal evidence bundles

```bash
tracecore bundle seal --latest
tracecore bundle seal --run <RUN_ID>
```

Use b

*[truncated — see source for full prompt]*