# VISION

> OpenClaw is the AI that actually does things.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## OpenClaw Vision

OpenClaw is the AI that actually does things.
It runs on your devices, in your channels, with your rules.

This document explains the current state and direction of the project.
We are still early, so iteration is fast.
Project overview and developer docs: [`README.md`](README.md)
Contribution guide: [`CONTRIBUTING.md`](CONTRIBUTING.md)

OpenClaw started as a personal playground to learn AI and build something genuinely useful:
an assistant that can run real tasks on a real computer.
It evolved through several names and shells: Warelay -> Clawdbot -> Moltbot -> OpenClaw.

The goal: a personal assistant that is easy to use, supports a wide range of platforms, and respects privacy and security.

The current focus is:

Priority:

- Security and safe defaults
- Bug fixes and stability
- Setup reliability and first-run UX

Next priorities:

- Supporting all major model providers
- Improving support for major messaging channels (and adding a few high-demand ones)
- Performance and test infrastructure
- Better computer-use and agent harness capabilities
- Ergonomics across CLI and web frontend
- Companion apps on macOS, iOS, Android, Windows, and Linux

Contribution rules:

- One PR = one issue/topic. Do not bundle multiple unrelated fixes/features.
- PRs over ~5,000 changed lines are reviewed only in exceptional circumstances.
- Do not open large batches of tiny PRs at once; each PR has review cost.
- For very small related fixes, grouping into one focused PR is encouraged.

## Security

Security in OpenClaw is a deliberate tradeoff: strong defaults without killing capability.
The goal is to stay powerful for real work while making risky paths explicit and operator-controlled.

Canonical security policy and reporting:

- [`SECURITY.md`](SECURITY.md)

We prioritize secure defaults, but also expose clear knobs for trusted high-power workflows.

## Plugins & Memory

OpenClaw has an extensive plugin API.
Core stays lean; optional capability should usually 

*[truncated — see source for full prompt]*