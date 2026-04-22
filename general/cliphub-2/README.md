# CLIPHUB

> **Download a company.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ClipHub — The Company Registry

**Download a company.**

ClipHub is the public registry where people share, discover, and download Paperclip company configurations. A company template is a portable artifact containing an entire org — agents, reporting structure, adapter configs, role definitions, seed tasks — ready to spin up with one command.

---

## What It Is

ClipHub is to Paperclip what a package registry is to a programming language. Paperclip already supports exportable org configs (see [SPEC.md](./SPEC.md) §2). ClipHub is the public directory where those exports live.

A user builds a working company in Paperclip — a dev shop, a marketing agency, a research lab, a content studio — exports the template, and publishes it to ClipHub. Anyone can browse, search, download, and spin up that company on their own Paperclip instance.

The tagline: **you can literally download a company.**

---

## What Gets Published

A ClipHub package is a **company template export** — the portable artifact format defined in the Paperclip spec. It contains:

| Component | Description |
|---|---|
| **Company metadata** | Name, description, intended use case, category |
| **Org chart** | Full reporting hierarchy — who reports to whom |
| **Agent definitions** | Every agent: name, role, title, capabilities description |
| **Adapter configs** | Per-agent adapter type and configuration (SOUL.md, HEARTBEAT.md, CLAUDE.md, process commands, webhook URLs — whatever the adapter needs) |
| **Seed tasks** | Optional starter tasks and initiatives to bootstrap the company's first run |
| **Budget defaults** | Suggested token/cost budgets per agent and per company |

Templates are **structure, not state.** No in-progress tasks, no historical cost data, no runtime artifacts. Just the blueprint.

### Sub-packages

Not every use case needs a whole company. ClipHub also supports publishing individual components:

- **Agent templates** — a single agent config (e.g. "Senior TypeScript Engineer", "SEO 

*[truncated — see source for full prompt]*